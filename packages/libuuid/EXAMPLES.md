# libuuid/libuuid examples

```php
use Pnlx\Libuuid\Libuuid;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libuuid = $runtime->load(Libuuid::class);

// uuid_t is typedef unsigned char[16].
// Allocate a uuid_t and a 37-byte output buffer using the pnl allocator.
$uuid = $runtime->allocator()->new('unsigned char[16]');
$buf  = $runtime->allocator()->new('char[37]');
$libuuid->uuid_generate($uuid);
$libuuid->uuid_unparse($uuid, $buf);
echo \FFI::string($buf, 36) . PHP_EOL;
// uuid_generate_random() and uuid_generate_time() select a specific variant.
```
