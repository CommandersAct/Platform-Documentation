# FR : Suppression des cookies lors du retrait du consentement

Lorsque l’utilisateur retire son consentement, il est parfois nécessaire de supprimer les cookies déposés précédemment (cas de la France notamment). Nous mettons à disposition un **script simple et personnalisable** qui permet de supprimer automatiquement les cookies **first-party** (déposés par votre propre site) et cookies tiers (via appel API)

Certains cookies spécifiques nécessitent une approche ciblée. Voici comment procéder étape par étape :

***

### **1. Identifier les cookies à conserver**

Avant toute chose, il vous faut lister les cookies indispensables au bon fonctionnement de votre site.\
Exemples de cookies techniques ou liés à la gestion du consentement à conserver :

* **TCPID**
* **TC\_PRIVACY**
* **TC\_PRIVACY\_CENTER**

👉 **Comment identifier ces cookies essentiels ?**\
Nous mettons à votre disposition la fonctionnalité [**Cookie Scanner**](../extensions/cookie-scanner.md), qui vous permet de lister les cookies présents sur votre site, pour vous aider à identifier ceux qui doivent être conservés. Cela évite d’en oublier et assure un bon fonctionnement après la suppression des cookies non essentiels.\
Il est conseillé de vérifier avec vos équipes techniques ou votre prestataire les cookies techniques qui ne doivent pas être supprimés.

> 💡 **Action :** Utilisez **Cookie Scanner** pour obtenir une liste complète des cookies présents sur votre site

***

### **2. Utiliser un script pour supprimer automatiquement les cookies non essentiels**

Nous proposons un **script JavaScript** simple et personnalisable qui se déclenche automatiquement lorsque l’utilisateur retire son consentement via la CMP Commanders Act.\
Le script réalise les actions suivantes :

* **Détection du retrait de consentement :**\
  Le script s’abonne à un événement de mise à jour du consentement. Dès que l’utilisateur opte pour le refus, le script se lance.
* **Suppression des cookies first-party :**\
  Il parcourt l’ensemble des cookies déposés par votre domaine et supprime ceux qui ne figurent pas dans votre liste blanche. Pour être efficace, il teste plusieurs variantes de domaine (votre domaine et ses sous-domaines).
*   **Optionnel – Appel de services côté serveur et partenaires :**\
    Le script peut également appeler des URL que vous aurez renseignées pour demander la suppression de cookies déposés **côté serveur** (cookies HTTP-only) ou par des **partenaires externes** (cookies tiers).\
    👉 **Voir le chapitre 3** pour en savoir plus sur la gestion des cookies HTTP-only et tiers.

    > ⚠️ **Note :** L’ajout de ces URL est facultatif. Si vous ne souhaitez pas utiliser cette fonctionnalité, il vous suffit de laisser le tableau des URL vide ou de supprimer cette partie du code. Vous pouvez aussi gérer ces suppressions par vous-même ou avec vos partenaires.

#### **📌 Où intégrer ce script ?**

Vous pouvez insérer ce code JavaScript :\
✅ **Dans la section "Custom JS" de la bannière Commanders Act** _(recommandé dans la plus part des cas)._\
✅ **Dans votre Tag Management System (TMS)** _(si vous souhaitez une gestion plus centralisée)._

**Télécharger le script JavaScript :**

<details>

<summary>Code JavaScript - suppression de cookies</summary>

```javascript
/**
 * This script listens for consent updates via the Commanders Act OnSite API.
 * When a user revokes consent (opt-out), it removes all 1st party cookies
 * except for those explicitly allowed. It also calls configured URLs to delete cookies
 * on the server side (e.g., httpOnly or third-party cookies).
 */
(function () {
  // List of cookies to retain (system cookies, technical storage items)
  var allowedCookies = ["TCPID", "TC_PRIVACY", "TC_PRIVACY_CENTER"];
  // Optional: Regex to match additional cookies or storage keys to retain
  var allowedCookiesPattern = /your_regex_[a-z0-9]*/; // Adjust this pattern if necessary

  // Array of server URLs to call for server-side deletion of cookies (httpOnly/partner cookies). Leave empty if you don't have such urls/api
  var serverDeletionUrls = [
    "https://server1.example.com/delete-cookies",
    "https://server2.example2.com/delete-cookies"
  ];

  // Subscribe to consent updates using the Commanders Act OnSite API
  cact("consent.onUpdate", function (consentData) {
    if (consentData.updateEvent === "revoked") {
      // Retrieve all cookies
      var allCookies = document.cookie.split(";").map(function (item) {
        return item.split("=")[0].trim();
      });
      // Determine which cookies need to be removed (i.e. not allowed)
      var cookiesForRemoval = allCookies.filter(function (cookieName) {
        return allowedCookies.indexOf(cookieName) === -1 && !allowedCookiesPattern.test(cookieName);
      });

      // Remove each cookie from all possible domain variants
      cookiesForRemoval.forEach(function (cookieName) {
        var hostParts = window.location.hostname.split(".");
        while (hostParts.length > 0) {
          var domainCandidate = "." + hostParts.join(".");
          tC.removeCookie(cookieName, domainCandidate);
          hostParts.shift();
        }
        // Also try removing the cookie without a domain specification
        tC.removeCookie(cookieName, "");
      });

      // Call server-side endpoints to delete httpOnly and partner cookies
      serverDeletionUrls.forEach(function (url) {
        // Use fetch with no-cors mode to trigger the deletion endpoints
        fetch(url, { mode: "no-cors" }).catch(function (error) {
          console.error("Error calling server deletion URL:", url, error);
        });
      });
    }
  });
})();
```

</details>

***

### **3. Supprimer les cookies créés côté serveur et les cookies tiers**

#### **Cookies HTTP-only sur votre domaine**

Certains cookies sont créés côté serveur et marqués comme **HTTP-only**. Ils ne sont pas accessibles par JavaScript et ne peuvent être supprimés que par le serveur.

* **Origine :** Ils peuvent être déposés par **vos propres serveurs** ou par un partenaire à qui vous avez délégué la gestion de votre domaine (via un **CNAME, un WAF, un proxy, etc.**).

👉 **Que pouvez-vous faire ?**

* **Créer une API sur votre serveur** pour supprimer ces cookies.
* **Ajouter l’URL de votre API dans le script**, afin qu’elle soit automatiquement appelée lors du retrait du consentement.

***

#### **Cookies tiers**

Ces cookies sont déposés par des services externes (publicité, analyses, widgets, etc.) et ne sont pas générés directement sur votre domaine.

* **Limitation :** Le script JavaScript ne peut pas supprimer directement ces cookies, sauf si ces fournisseurs offrent une API ou une URL dédiée permettant leur suppression.
* **Que faire ?**\
  👉 **Demandez à vos partenaires** s’ils proposent un mécanisme de suppression (API ou URL dédiée).\
  Si c’est le cas, ajoutez ces URL dans le script pour automatiser leur appel lors du retrait du consentement. Sinon, envisagez de ne plus charger ces services après un refus de consentement via votre Tag Management System.

***

### **4. Ce que fait (et ne fait pas) notre script**

✅ **Il supprime automatiquement les cookies déposés sur votre domaine** (**first-party**), en conservant ceux que vous avez explicitement listés.\
✅ **Il permet d’appeler des URL de suppression** pour les **cookies HTTP-only** **et tiers** (optionnel).\
❌ **Il ne peut pas supprimer directement les cookies tiers**, sauf si ces derniers proposent une url ou API dédiée.\
❌ **Il ne peut pas supprimer les cookies HTTP-only**, sauf si ces derniers proposent une url ou API dédiée.
