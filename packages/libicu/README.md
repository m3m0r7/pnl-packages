# ICU Package

Package: `libicu/libicu`

Base library: ICU

License: ICU

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libicu
```

The package requires ICU headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libicu\Libicu;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libicu = $runtime->load(Libicu::class);

// Query the ICU library version
$verBuf = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$libicu->u_getVersion($verBuf);
echo "ICU version: " . $verBuf[0] . "." . $verBuf[1] . "\n";

// Normalize a Unicode string to NFC using unorm2
// $norm = $libicu->unorm2_getNFCInstance($error);
// $libicu->unorm2_normalize($norm, $src, -1, $dest, $destCapacity, $error);
```

This snippet is printed when `pnl install libicu` finishes — it comes from the package's `examples` field in `pnlx.json`.
