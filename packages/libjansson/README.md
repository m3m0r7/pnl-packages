# Jansson Package

Package: `libjansson/libjansson`

Base library: Jansson

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libjansson
```

The package requires Jansson headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libjansson\Libjansson;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libjansson = $runtime->load(Libjansson::class);

// Parse a JSON string and read a value from it.
$root = $libjansson->json_loads('{"name":"pnl","version":1}', 0, null);
$nameVal = $libjansson->json_object_get($root, 'name');
$name = $libjansson->json_string_value($nameVal); // returns string "pnl"
echo $name . PHP_EOL;
$libjansson->json_decref($root);
```

This snippet is printed when `pnl install libjansson` finishes — it comes from the package's `examples` field in `pnlx.json`.
