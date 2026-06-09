# Duktape Package

Package: `libduktape/libduktape`

Base library: Duktape

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libduktape
```

The package requires Duktape headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libduktape` finishes — it comes from the package's `examples` field in `pnlx.json`.
