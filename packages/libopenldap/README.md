# OpenLDAP Package

Package: `libopenldap/libopenldap`

Base library: OpenLDAP

License: OLDAP-2.8

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libopenldap
```

The package requires the OpenLDAP headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libopenldap\Libopenldap;

// ldap_err2string() maps an LDAP result code to its human-readable message.
echo Libopenldap::ldap_err2string(0) . PHP_EOL; // "Success"
```

This snippet is printed when `pnl install libopenldap` finishes — it comes from the
package's `examples` field in `pnlx.json`.
