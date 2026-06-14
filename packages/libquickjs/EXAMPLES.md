# libquickjs/libquickjs examples

```php
use Pnlx\Libquickjs\Libquickjs;
use function Pnlx\Util\is_null;

$libquickjs = new Libquickjs();

// Create a QuickJS runtime and context
$jsRuntime = $libquickjs->JS_NewRuntime();
if (is_null($jsRuntime)) {
    throw new \RuntimeException('JS_NewRuntime failed');
}
$ctx = $libquickjs->JS_NewContext($jsRuntime);
if (is_null($ctx)) {
    $libquickjs->JS_FreeRuntime($jsRuntime);
    throw new \RuntimeException('JS_NewContext failed');
}

// Evaluate a JavaScript expression
$val = $libquickjs->JS_Eval($ctx, '1 + 2', 5, '<input>', 0);
$str = $libquickjs->JS_ToCString($ctx, $val);
echo "Result: {$str}\n"; // 3
$libquickjs->JS_FreeCString($ctx, $str);
$libquickjs->JS_FreeValue($ctx, $val);

$libquickjs->JS_FreeContext($ctx);
$libquickjs->JS_FreeRuntime($jsRuntime);
```
