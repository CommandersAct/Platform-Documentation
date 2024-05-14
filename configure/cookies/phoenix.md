# Phoenix

Phoenix reduce the impact of Safari ITP on your cookies.

### Overview <a href="#overview" id="overview"></a>

The Intelligent Tracking Protection (ITP) feature of Safari browsers reduces the duration of most 1st party cookies to one day. ITP was initially implemented to reduce the effectiveness of cross domain visitor tracking—unfortunately it also has a strong impact on the user experience of website users. 1st party cookies are often used to store user settings of important features of a website.

e.g. cookie banner use 1st party cookies to store consent settings of a website visitor. On Safari these cookies might only last for one day. Thus cookie banner show up on almost any consecutive website visit, asking the visitor for his privacy settings again and again.

Phoenix enables you to persist 1st party cookies for longer durations to reduce the impact of ITP on your website and business.

#### Which cookies can be persisted with Phoenix? <a href="#which-cookies-can-be-persisted-with-phoenix" id="which-cookies-can-be-persisted-with-phoenix"></a>

To understand how Phoenix works it is important to understand following cookie concepts.

1st party vs. 3rd party cookiesSecure Http cookies

A cookie belongs to a domain (e.g. `site.com`). A cookies set on `site-a.com` belongs to `site-a.com`, a cookie set on `site-b.com` belongs to `site-b.com`.

A cookie is a 1st party cookie or a 3rd party cookie depending on the relation of the website domain and the cookie domain.

In case a visitor goes to `site-a.com` the browser loads all cookies set on `site-a.com` as 1st party cookies. When `site-a.com` implements a service from `site-b.com` (e.g. web analytics or a cookie banner) the browser might load cookies from `site-b.com` as 3rd party cookies.

You can inspect the domain of a cookie in the Developer Tools of most browsers. In Chrome browser you can open the Developer Tools by navigation to `View > Developer > Developer Tools`. You will find a list of all cookies in the Developer Tool under `Application > Cookies > Your Domain`.

![](https://community.commandersact.com/\~gitbook/image?url=https%3A%2F%2F2813015996-files.gitbook.io%2F%7E%2Ffiles%2Fv0%2Fb%2Fgitbook-legacy-files%2Fo%2Fassets%252F-LdtBYhZj-wxWhoZaUXI%252F-M6ZOPE1Qlc3RbEzC8Sk%252F-M6ZPo1DityO6Ay8ofYT%252Fcookie-domain-in-developer-tools.png%3Falt%3Dmedia%26token%3D36e15aa6-31dc-40d4-b12c-c9c33697459e\&width=768\&dpr=4\&quality=100\&sign=e3bfc2b696251fe01ab421b386d4c3a4e69427a372611757c1070ccf5be8b2cb)Example of a 1st party cookie. The visitor is on www.commandersact.com which matches the cookie domain of .commandersact.com.

A cookie is a 1st party cookie in case the field "Domain" matches the domain of the current website (e.g. a cookie with a domain `.site.com` is a 1st party cookie on a website with the domain `www.site.com`).

3rd party cookies are blocked by many browsers (e.g. Safari and Firefox) and will most likely be blocked by all major browsers in 2022. Phoenix works with 1st party cookies.

Phoenix allows to persist 1st party cookies without a Secure and HttpOnly flag.

#### How does Phoenix persist cookies? <a href="#how-does-phoenix-persist-cookies" id="how-does-phoenix-persist-cookies"></a>

After Phoenix is set up on a website domain it will backup selected 1st party cookies that are affected by ITP by storing them in Secure Http cookies that are not affected by ITP.

Phoenix will check if a 1st party cookie was deleted and recreate it from its backup on further website visits. Therefore the 1st party cookie is not anymore affected by ITP.

### Setup <a href="#setup" id="setup"></a>

Phoenix setup consists of following steps. A Commanders Act consultant will support you during setup.

<figure><img src="../../.gitbook/assets/image (511).png" alt=""><figcaption></figcaption></figure>

Example configuration of a Phoenix subdomain and cookie size limit.

#### Configure Phoenix Subdomain <a href="#configure-phoenix-subdomain" id="configure-phoenix-subdomain"></a>

Phoenix has to run on your website domain to be able to create Secure Http cookies. Therefore you will need to assign a subdomain of your domain (e.g. `phoenix.mydomain.com`) to Phoenix.

In case you want to activate Phoenix for multiple domains (e.g. two domains, one `.com` for an English site and `.fr` for a French site.) you need to create one subdomain per domain.

Your administrator can configure your Phoenix subdomains in your Commanders Act interface under `Admin > Domain Management`.

#### Configure Cookie Size Limit <a href="#configure-cookie-size-limit" id="configure-cookie-size-limit"></a>

Browsers, like Safari, can usually store a **maximum of 8 kB** of cookie data per domain. Web servers also have a cookie data limit, often matching the 8 kB of browsers.

Your administrator can configure how much cookie space he wants to make available for Phoenix in your Commanders Act interface under `Admin > Domain Management`. **It is recommended to not exceed 2 kB, and we suggest a limit below 0.5 kB during initial setup**.

Exceeding cookie storage limit can make your website inaccessible. Please consult with your technical teams during setup to define an optimal storage quota for Phoenix.

#### Setup CNAME Domain Record <a href="#setup-cname-domain-record" id="setup-cname-domain-record"></a>

You will then need to connect your Phoenix subdomains with the Phoenix service. Your domain administrator needs to therefore configure CNAME entries that point your Phoenix subdomains (e.g. `phoenix.mydomain.com`) to the Phoenix service domain (e.g. `sitexxx.commander5.com`).

Your administrator can find the Phoenix service domain in your Commanders Act interface under `Admin > Domain Management`.

You have to re-generate your web containers (Commanders Act TMS) after enabling Phoenix.

### Managing Cookies with Phoenix <a href="#managing-cookies-with-phoenix" id="managing-cookies-with-phoenix"></a>

Commanders Act cookies are automatically managed by Phoenix. Cookies of other vendors have to be configured manually.

#### Commanders Act TMS <a href="#tagcommander" id="tagcommander"></a>

In TMS Commanders Act cookies are usually set by your vendor tags. You can enable Phoenix for selected tags in the "Deployment" step of your Commanders Act TMS container by enabling the `ITP BYPASS` option. This will automatically persist all cookies of this tag with Phoenix. A progress bar will show the remaining cookie space made available by your administrator.

Example how cookies a of Tag are persisted with Phoenix

<figure><img src="../../.gitbook/assets/demo_cookies_phoenix (1).gif" alt=""><figcaption></figcaption></figure>

Please contact the Commanders Act support or your Commanders Act consultant in case the ITP BYPASS option is not available for a tag or cookie you would like to persist.

#### Other Systems <a href="#other-systems" id="other-systems"></a>

Please contact your Commanders Act consultant in case you would like to persist cookies outside of Commanders Act TMS or in case you would like to install Phoenix without Commanders Act TMS.
