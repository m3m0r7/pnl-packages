# libnettle cipher registry

Enumerate the block ciphers compiled into Nettle with `nettle_get_ciphers()`, reading each algorithm's key and block size straight off the C struct, and confirm the MAC registry with `nettle_get_macs()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnettle\Libnettle;
use function Pnlx\Util\is_null;

// nettle_get_ciphers() returns the NULL-terminated registry of block ciphers
// the library was built with: a C `const struct nettle_cipher * const *`.
$ciphers = Libnettle::nettle_get_ciphers();
if (is_null($ciphers)) {
    echo "no cipher registry\n";
    return;
}

// Walk the array of struct pointers, reading metadata straight off each entry.
$arr = $ciphers->cdata();
for ($i = 0; !is_null($arr[$i]); $i++) {
    $c = $arr[$i];
    printf("%s: key_size=%d block_size=%d\n", \FFI::string($c->name), $c->key_size, $c->block_size);
}

// nettle_get_macs() exposes the MAC algorithm registry in the same way.
$macs = Libnettle::nettle_get_macs();
echo !is_null($macs) ? "mac registry loaded\n" : "no macs\n";
```
