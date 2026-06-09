# GD Package

Package: `libgd/libgd`

Base library: GD

License: GD

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libgd
```

The package requires GD headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libgd\Libgd;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libgd = $runtime->load(Libgd::class);

// Create a 200x100 true-colour image, draw a filled red rectangle, save as PNG.
$image = $libgd->gdImageCreateTrueColor(200, 100);
if (is_null($image)) {
    throw new \RuntimeException('gdImageCreateTrueColor() failed');
}

$red  = $libgd->gdImageColorAllocate($image, 255, 0, 0);
$libgd->gdImageFilledRectangle($image, 0, 0, 199, 99, $red);

// gdImagePngPtr(image, &size) returns a PNG blob in memory.
$allocator = $runtime->allocator();
$size = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$png = $libgd->gdImagePngPtr($image, $size);
echo "PNG blob: " . $size->cdata . " bytes" . PHP_EOL;

$libgd->gdFree($png);
$libgd->gdImageDestroy($image);
```

This snippet is printed when `pnl install libgd` finishes — it comes from the package's `examples` field in `pnlx.json`.
