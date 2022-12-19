# Web container generator

### Release v78.0 - 13/12/2022

* Update `tC.setCookie` to encode `!'()~` characters in the cookie value. This is a requirement for WAF restrictions of some TagCommander users.

### Release v77.0 - 01/12/2022

* Update `tC.privacy.hit` to not send hits when analytics category was refused using consent JS OnSite API 

### Release v76.1 - 30/11/2022
* Update `trigger` JS OnSite API to better use source-keys in multi-container contexts

### Release v76.0 - 15/11/2022
* Update `tC.setCookie` to use `encodeURIComponent` instead of `escape` (deprecated)
