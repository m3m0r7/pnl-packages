# libopenldap/libopenldap examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libopenldap\Libopenldap;

// ldap_err2string() maps an LDAP result code to its human-readable message.
echo Libopenldap::ldap_err2string(0) . PHP_EOL; // "Success"
```
