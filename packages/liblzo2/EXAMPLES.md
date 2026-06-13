# liblzo2/liblzo2 examples

```php
use Pnlx\Liblzo2\Liblzo2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$liblzo2 = $runtime->load(Liblzo2::class);

// lzo_version_string() returns the LZO release, e.g. "2.10".
$version = $liblzo2->lzo_version_string();
echo "LZO: $version\n";

// Explore further: lzo1x_1_compress(), lzo1x_decompress_safe(),
// lzo_adler32(), lzo_init(), ...
```
