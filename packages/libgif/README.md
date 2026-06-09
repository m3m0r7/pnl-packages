# giflib Package

Package: `libgif/libgif`

Base library: giflib

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libgif
```

The package requires giflib headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libgif\Libgif;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libgif = $runtime->load(Libgif::class);

// Open a GIF file for reading (returns GifFileType* handle)
$error = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$gif = $libgif->DGifOpenFileName('animation.gif', $error);
if (is_null($gif)) {
    echo "Could not open GIF (error code: " . $error[0] . ")\n";
} else {
    $libgif->DGifSlurp($gif);
    echo "Image count: " . $gif->ImageCount . "\n";
    $libgif->DGifCloseFile($gif, $error);
}
```

This snippet is printed when `pnl install libgif` finishes — it comes from the package's `examples` field in `pnlx.json`.
