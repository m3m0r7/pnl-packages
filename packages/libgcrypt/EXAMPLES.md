# libgcrypt/libgcrypt examples

```php
use Pnlx\Libgcrypt\Libgcrypt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libgcrypt = $runtime->load(Libgcrypt::class);

// Check the runtime version (returns null if requirement not met).
$version = $libgcrypt->gcry_check_version(null);
echo "libgcrypt version: " . $version . PHP_EOL;

// Hash a string with SHA-256.
// GCRY_MD_SHA256 = 8, GCRY_MD_FLAG_SECURE = 2
$allocator = $runtime->allocator();
$hd = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libgcrypt->gcry_md_open($hd, 8, 0);
$data = "Hello, world!";
$libgcrypt->gcry_md_write($hd->cdata, $data, strlen($data));
$libgcrypt->gcry_md_final($hd->cdata);
// gcry_md_read(hd, algo) returns a pointer to the digest buffer.
$libgcrypt->gcry_md_close($hd->cdata);
echo "SHA-256 hash computed." . PHP_EOL;
```
