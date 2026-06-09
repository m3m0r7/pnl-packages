# QuickJS Package

Package: `libquickjs/libquickjs`

Base library: QuickJS

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libquickjs
```

The package requires QuickJS headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libquickjs\Libquickjs;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libquickjs = $runtime->load(Libquickjs::class);

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

This snippet is printed when `pnl install libquickjs` finishes — it comes from the package's `examples` field in `pnlx.json`.
