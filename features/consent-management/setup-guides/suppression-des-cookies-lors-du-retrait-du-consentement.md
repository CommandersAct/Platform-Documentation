# Cookie deletion upon consent withdrawal

When a user withdraws consent, it may be necessary to delete previously set cookies (notably in France). We provide a **simple and customizable solution** to automatically remove **first-party cookies** (set by your own domain) and optionally trigger deletion of server-side or third-party cookies via API calls.

Some specific cookies require a targeted approach. Follow the steps below:

***

### **1. Identify cookies to keep**

First, list the cookies required for your website to function properly.  
Examples of technical or consent-related cookies to retain:

* **TCPID**
* **TC_PRIVACY**
* **TC_PRIVACY_CENTER**

👉 **How to identify essential cookies?**  
We provide the [**Realtime Cookie Scanner**](https://doc.commandersact.com/features/realtime-cookie-scanner), which lists all cookies present on your site to help you identify which ones must be preserved.  
It is recommended to validate this list with your technical teams or providers.

> 💡 **Action:** Use **Cookie Scanner** to get a complete inventory of cookies on your site.

***

### **2. Automatically delete non-essential cookies**

Depending on your setup, use one of the following approaches:

---

#### **2.1 If you use Commanders Act TMS (recommended)**

Use the tag **"Commanders Act - Cookie Cleanup Tag"** available in the tag gallery.

This tag:
* Automatically listens to consent withdrawal events
* Removes all non-essential first-party cookies
* Handles domain variations
* Allows configuration of server-side deletion endpoints if needed

👉 This is the **simplest and recommended approach**, requiring no custom code.

---

#### **2.2 If you use another TMS (GTM, etc.) or custom implementation**

Use the JavaScript script below. It listens for consent withdrawal and performs the following actions:

* Detects consent withdrawal
* Deletes first-party cookies not in your allowlist
* Optionally calls server-side endpoints to delete HTTP-only or third-party cookies

**Integration:**
You can add this script:
* In your CMP custom JavaScript section
* In your Tag Management System (GTM, etc.)

**JavaScript code:**

```javascript
(function () {
  var allowedCookies = ["TCPID", "TC_PRIVACY", "TC_PRIVACY_CENTER"];
  var allowedCookiesPattern = /your_regex_[a-z0-9]*/;

  var serverDeletionUrls = [
    "https://server1.example.com/delete-cookies",
    "https://server2.example2.com/delete-cookies"
  ];

  window.addEventListener("consent.withdrawn", function () {
    var allCookies = document.cookie.split(";").map(function (item) {
      return item.split("=")[0].trim();
    });

    var cookiesForRemoval = allCookies.filter(function (cookieName) {
      return allowedCookies.indexOf(cookieName) === -1 && !allowedCookiesPattern.test(cookieName);
    });

    cookiesForRemoval.forEach(function (cookieName) {
      var hostParts = window.location.hostname.split(".");
      while (hostParts.length > 0) {
        var domainCandidate = "." + hostParts.join(".");
        document.cookie = cookieName + "=;expires=Thu, 01 Jan 1970 00:00:01 GMT;path=/;domain=" + domainCandidate;
        hostParts.shift();
      }
      document.cookie = cookieName + "=;expires=Thu, 01 Jan 1970 00:00:01 GMT;path=/";
    });

    serverDeletionUrls.forEach(function (url) {
      fetch(url, { mode: "no-cors" }).catch(function () {});
    });
  });
})();
```

***

### **3. Deleting server-side and third-party cookies**

#### **HTTP-only cookies (server-side)**

Some cookies are created server-side and marked as **HTTP-only**, making them inaccessible to JavaScript.

* **Origin:** Your servers or delegated infrastructure (CNAME, proxy, WAF, etc.)

👉 **What to do:**
* Implement an API on your server to delete these cookies
* Add the API endpoint to your cleanup configuration

---

#### **Third-party cookies**

These cookies are set by external services (ads, analytics, widgets, etc.).

* **Limitation:** JavaScript cannot directly delete them

👉 **What to do:**
* Ask providers if they offer a deletion API or endpoint
* If available, call these endpoints when consent is withdrawn
* Otherwise, rely on the provider’s own consent mechanisms

***

### **4. What this solution does (and does not do)**

✅ Deletes first-party cookies on your domain (except allowlisted ones)  
✅ Can trigger deletion of HTTP-only and third-party cookies via API calls  
❌ Cannot directly delete third-party cookies without provider support  
❌ Cannot directly delete HTTP-only cookies without server-side implementation  
