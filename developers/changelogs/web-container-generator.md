# Web container generator

### Release v78.0 - 13/12/2022

* Update `tC.setCookie` function to encode `!'()~` characters in the cookie value. This is a requirement for WAF restrictions of some TagCommander users.

### Release v77.0 - 01/12/2022

* Update `tC.privacy.hit` function to not send hits when analytics category was refused using consent JS OnSite API

### Release v76.1 - 30/11/2022

* Update `trigger` JS OnSite API to better use source-keys in multi-container contexts

### Release v76.0 - 15/11/2022

* Update `tC.setCookie` function to use `encodeURIComponent` on the content of the cookie, instead of `escape` .\
  `escape` function is deprecated and cannot be maintain anymore, more information [here](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global\_Objects/escape).
