# libuuid/libuuid examples

```php
use Pnlx\Libuuid\Libuuid;

// uuid_t is typedef unsigned char[16].
// Allocate a uuid_t and a 37-byte output buffer using the pnl allocator.
$uuid = (new \Pnlx\FFI\Allocator())->new('unsigned char[16]');
$buf  = (new \Pnlx\FFI\Allocator())->new('char[37]');
Libuuid::uuid_generate($uuid);
Libuuid::uuid_unparse($uuid, $buf);
echo \FFI::string($buf, 36) . PHP_EOL;
// uuid_generate_random() and uuid_generate_time() select a specific variant.
```
