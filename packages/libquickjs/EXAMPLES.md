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

// Evaluate a JavaScript expression. JS_Eval returns a JSValue *by value* (a small
// struct), handed back as a typed value.
$val = Libquickjs::JS_Eval($ctx, '1 + 2', 5, '<input>', 0);
// Convert it to a C string. JS_ToCString is `static inline` (no exported symbol),
// so call the exported JS_ToCStringLen2 it wraps (NULL length out-param, cesu8 = 0).
$len = null;
$str = Libquickjs::JS_ToCStringLen2($ctx, $len, $val, 0);
echo "Result: {$str}\n"; // 3
// Notes on cleanup: pnl returns $str as a PHP-string copy (not the original C
// pointer), so there is nothing to JS_FreeCString. The result here is an integer
// JSValue, which is not reference-counted — quickjs's `static inline` JS_FreeValue
// would skip freeing it (only the exported __JS_FreeValue exists, and it must not be
// called on a non-refcounted value), so no value free is needed. Tearing down the
// context and runtime releases everything.
Libquickjs::JS_FreeContext($ctx);
Libquickjs::JS_FreeRuntime($jsRuntime);
```
