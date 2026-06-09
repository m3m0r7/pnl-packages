# hiredis Package

Package: `libhiredis/libhiredis`

Base library: hiredis

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libhiredis
```

The package requires hiredis headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libhiredis` finishes — it comes from the package's `examples` field in `pnlx.json`.
