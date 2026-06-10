# libduktape/libduktape examples

```php
use Pnlx\Libduktape\Libduktape;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libduktape = $runtime->load(Libduktape::class);

// Create a Duktape heap and evaluate a JavaScript expression.
$ctx = $libduktape->duk_create_heap_default();
if (is_null($ctx)) {
    throw new \RuntimeException('Failed to create Duktape heap');
}

$libduktape->duk_eval_string($ctx, "1 + 2");
$result = $libduktape->duk_get_number($ctx, -1);
echo "1 + 2 = " . $result . PHP_EOL;   // 3

$libduktape->duk_pop($ctx);
$libduktape->duk_destroy_heap($ctx);
```
