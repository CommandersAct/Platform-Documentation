# Web container generator

### Release v78.0 - 13/12/2022

* Update tC.setCookie to use `encodeURIComponent` instead of `escape` (deprecated)
* Update tC.setCookie to encode `!'()~` characters in the cookie value. This is a requirement for WAF restrictions of some TagCommander users.
