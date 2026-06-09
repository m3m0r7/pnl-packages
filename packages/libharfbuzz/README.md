# HarfBuzz Package

Package: `libharfbuzz/libharfbuzz`

Base library: HarfBuzz

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libharfbuzz
```

The package requires HarfBuzz headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libharfbuzz\Libharfbuzz;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libharfbuzz = $runtime->load(Libharfbuzz::class);

// Query HarfBuzz version
$versionStr = $libharfbuzz->hb_version_string();
echo "HarfBuzz: " . $versionStr . "\n";

// Create a shaping buffer, add text, then destroy it
$buf = $libharfbuzz->hb_buffer_create();
$libharfbuzz->hb_buffer_add_utf8($buf, 'Hello', -1, 0, -1);
$libharfbuzz->hb_buffer_guess_segment_properties($buf);
// Shape with a font: $libharfbuzz->hb_shape($font, $buf, null, 0);
$libharfbuzz->hb_buffer_destroy($buf);
```

This snippet is printed when `pnl install libharfbuzz` finishes — it comes from the package's `examples` field in `pnlx.json`.
