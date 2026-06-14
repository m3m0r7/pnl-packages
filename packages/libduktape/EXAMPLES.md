# libduktape/libduktape examples

```php
use Pnlx\Libduktape\Libduktape;
use function Pnlx\Util\is_null;

// Create a Duktape heap and evaluate a JavaScript expression.
$ctx = Libduktape::duk_create_heap_default();
if (is_null($ctx)) {
    throw new \RuntimeException('Failed to create Duktape heap');
}

Libduktape::duk_eval_string($ctx, "1 + 2");
$result = Libduktape::duk_get_number($ctx, -1);
echo "1 + 2 = " . $result . PHP_EOL;   // 3

Libduktape::duk_pop($ctx);
Libduktape::duk_destroy_heap($ctx);
```
