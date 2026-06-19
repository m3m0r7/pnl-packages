# libquickjs/libquickjs examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libquickjs\Libquickjs;
use function Pnlx\Util\is_null;

// Create a QuickJS runtime and context
$jsRuntime = Libquickjs::JS_NewRuntime();
if (is_null($jsRuntime)) {
    throw new \RuntimeException('JS_NewRuntime failed');
}
$ctx = Libquickjs::JS_NewContext($jsRuntime);
if (is_null($ctx)) {
    Libquickjs::JS_FreeRuntime($jsRuntime);
    throw new \RuntimeException('JS_NewContext failed');
}

// Evaluate a JavaScript expression
$val = Libquickjs::JS_Eval($ctx, '1 + 2', 5, '<input>', 0);
$str = Libquickjs::JS_ToCString($ctx, $val);
echo "Result: {$str}\n"; // 3
Libquickjs::JS_FreeCString($ctx, $str);
Libquickjs::JS_FreeValue($ctx, $val);

Libquickjs::JS_FreeContext($ctx);
Libquickjs::JS_FreeRuntime($jsRuntime);
```
