# libhiredis/libhiredis examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhiredis\Libhiredis;
use function Pnlx\Util\is_null;

// Connect to Redis (needs a server on 127.0.0.1:6379). redisContext is a generated
// struct, so its `err` field is read through the typed accessor getErr() — nonzero
// means the connection failed.
$ctx = Libhiredis::redisConnect('127.0.0.1', 6379);
if (!is_null($ctx) && $ctx->getErr() === 0) {
    // redisCommand returns `void *` (really a redisReply*). Re-wrap it as the
    // generated redisReply type to read its fields.
    $reply = Libhiredis::redisCommand($ctx, 'PING');
    if (!is_null($reply)) {
        $reply = new \Pnlx\Libhiredis\Types\redisReply($reply->cdata());
        echo "Redis reply: " . \Pnlx\Util::cString($reply->getStr()) . "\n";
    }
    Libhiredis::redisFree($ctx);
}
```
