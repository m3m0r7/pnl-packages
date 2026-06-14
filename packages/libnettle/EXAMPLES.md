# libnettle/libnettle examples

```php
use Pnlx\Libnettle\Libnettle;

// Query the library version
$major = Libnettle::nettle_version_major(); // returns int
$minor = Libnettle::nettle_version_minor(); // returns int
echo "Nettle version: $major.$minor\n";

// Compute a SHA-256 digest using the unprefixed algorithm functions
$ctx = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
Libnettle::sha256_init($ctx);
Libnettle::sha256_update($ctx, strlen('hello'), 'hello');
$digest = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
Libnettle::sha256_digest($ctx, 32, $digest);
```
