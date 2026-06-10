# libhiredis/libhiredis examples

```php
use Pnlx\Libhiredis\Libhiredis;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libhiredis = $runtime->load(Libhiredis::class);

// Connect to Redis, run a PING command, then disconnect
$ctx = $libhiredis->redisConnect('127.0.0.1', 6379);
if (!is_null($ctx) && $ctx->err === 0) {
    $reply = $libhiredis->redisCommand($ctx, 'PING');
    if (!is_null($reply)) {
        echo "Redis reply: " . $reply->str . "\n";
        $libhiredis->freeReplyObject($reply);
    }
    $libhiredis->redisFree($ctx);
}
```
