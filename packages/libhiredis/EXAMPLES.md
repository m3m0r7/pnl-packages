# libhiredis/libhiredis examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhiredis\Libhiredis;
use function Pnlx\Util\is_null;

// Connect to Redis, run a PING command, then disconnect
$ctx = Libhiredis::redisConnect('127.0.0.1', 6379);
if (!is_null($ctx) && $ctx->cdata()->err === 0) {
    $reply = Libhiredis::redisCommand($ctx, 'PING');
    if (!is_null($reply)) {
        echo "Redis reply: " . $reply->cdata()->str . "\n";
        Libhiredis::freeReplyObject($reply);
    }
    Libhiredis::redisFree($ctx);
}
```
