# libopenldap/libopenldap URL classification

Use the `ldap_is_*_url()` helpers to recognise LDAP and LDAPS URLs before opening a connection.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libopenldap\Libopenldap;

// ldap_is_ldap_url() classifies a string as a valid LDAP URL (1) or not (0).
$url = 'ldap://ldap.example.com/dc=example,dc=com';
$isLdap = Libopenldap::ldap_is_ldap_url($url);
$isLdap = is_object($isLdap) ? $isLdap->toInt() : $isLdap;
echo "ldap_is_ldap_url('$url') = $isLdap\n";

// ldap_is_ldaps_url() recognises the TLS-secured ldaps:// scheme.
$secure = 'ldaps://secure.example.com/dc=example,dc=com';
$isLdaps = Libopenldap::ldap_is_ldaps_url($secure);
$isLdaps = is_object($isLdaps) ? $isLdaps->toInt() : $isLdaps;
echo "ldap_is_ldaps_url('$secure') = $isLdaps\n";

// A non-LDAP URL is rejected by ldap_is_ldap_url().
$other = 'http://www.example.com/';
$notLdap = Libopenldap::ldap_is_ldap_url($other);
$notLdap = is_object($notLdap) ? $notLdap->toInt() : $notLdap;
echo "ldap_is_ldap_url('$other') = $notLdap\n";
```
