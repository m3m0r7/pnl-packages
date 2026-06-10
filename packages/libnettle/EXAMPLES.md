# libnettle/libnettle examples

```php
use Pnlx\Libnettle\Libnettle;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnettle = $runtime->load(Libnettle::class);

// Query the library version
$major = $libnettle->nettle_version_major(); // returns int
$minor = $libnettle->nettle_version_minor(); // returns int
echo "Nettle version: $major.$minor\n";

// Compute a SHA-256 digest using the unprefixed algorithm functions
$ctx = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libnettle->sha256_init($ctx);
$libnettle->sha256_update($ctx, strlen('hello'), 'hello');
$digest = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libnettle->sha256_digest($ctx, 32, $digest);
```
