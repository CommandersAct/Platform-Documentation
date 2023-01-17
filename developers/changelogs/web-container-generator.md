# Web container generator

### Release v80.0 - 17/01/2023

* Add new Consent OnSite API commands:
  * `consent.onReady`
  * `consentBanner.show`
  * `consentBanner.hide`
  * `consentCenter.show`
  * `consentCenter.hide`

### Release v79.1 - 16/01/2023

* Refactoring on the Privacy Banners

### Release v79.0 - 12/01/2023

* Refactoring on the tC object initialization

### Release v78.0 - 13/12/2022

* Update `tC.setCookie` to encode `!'()~` characters in the cookie value. This is a requirement for WAF restrictions of some TagCommander users.

### Release v77.0 - 01/12/2022

* Update `tC.privacy.hit` to not send hits when analytics category was refused using consent JS OnSite API

### Release v76.1 - 30/11/2022
* Update `trigger` JS OnSite API to better use source-keys in multi-container contexts

### Release v76.0 - 15/11/2022
* Update `tC.setCookie` to use `encodeURIComponent` instead of `escape` (deprecated)