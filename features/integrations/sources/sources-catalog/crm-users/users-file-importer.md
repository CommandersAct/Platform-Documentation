# Users file importer

### File structure <a href="#data-importcrm-filestructure" id="data-importcrm-filestructure"></a>

* One line per user
* Header on the file is needed for the matching
* Encoding: utf8
* The variable can not be calculated. It must be one line, one variable
* PGP or GPG key encryption are not supported. Files must be unencrypted before import.



Variables :&#x20;

* it must be the same name of data variable (Variables are in uppercase, they will transcribe automatically in lowercase)
* You can add new variables. Don't forget to define them in DataCommander variable interface
* The CRM variables should be prefixed with "person." and custom variables by "person.custom."

### File example

{% file src="../../../../../.gitbook/assets/CRM_IMPORT_V3.1.xlsx" %}
