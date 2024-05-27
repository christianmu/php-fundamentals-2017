Es bestehen 3 Möglichkeiten Fehlermeldungen ein- oder auszuschalten:

**1\. in der php.ini** mit einer dieser Einstellungen:

- **E_ALL** (ist die [Standardeinstellung](https://php.watch/versions/8.0/error-display-E_ALL) ab PHP 8.0. Show all errors, warnings and notices including coding standards.)
- **error_reporting = E_ALL & ~E_DEPRECATED & ~E_STRICT** (war die Standardeinstellung vor PHP 8.0)
- E_ALL & ~E_NOTICE (Show all errors, except for notices)
- E_ALL & ~E_NOTICE & ~E_STRICT (Show all errors, except for notices and coding standards warnings.)
- E_COMPILE_ERROR|E_RECOVERABLE_ERROR|E_ERROR|E_CORE_ERROR (Show only errors)

**2\. in der aktuellen Datei:**
damit Folgendes wirksam ist, muss zusätzlich in der _php.ini_ `display_errors = on` ermöglicht worden sein

- `ini_set('display_errors', 1);`
- `ini_set('display_startup_errors', 1);`
- `error_reporting(E_ALL);`

**3\. in einer separaten Konfigurationsdatei** (Best Practice):
für den Fall, dass man seinen Code auf einen Produktionsserver hochlädt und vergisst, die Fehlermeldungen der Einstellungen des Entwicklungsservers anzupassen:

```php
define('DEBUG', true);
error_reporting(E_ALL);
if(DEBUG == true)
{
       display_errors(true);
       log_errors(false);
}
else
{
      display_errors(false);
       log_errors(true);
}
```
