# libgd/libgd examples

```php
use Pnlx\Libgd\Libgd;
use function Pnlx\Util\is_null;

$libgd = new Libgd();

// Create a 200x100 true-colour image, draw a filled red rectangle, save as PNG.
$image = $libgd->gdImageCreateTrueColor(200, 100);
if (is_null($image)) {
    throw new \RuntimeException('gdImageCreateTrueColor() failed');
}

$red  = $libgd->gdImageColorAllocate($image, 255, 0, 0);
$libgd->gdImageFilledRectangle($image, 0, 0, 199, 99, $red);

// gdImagePngPtr(image, &size) returns a PNG blob in memory.
$allocator = (new \Pnlx\FFI\Allocator());
$size = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$png = $libgd->gdImagePngPtr($image, $size);
echo "PNG blob: " . $size->cdata . " bytes" . PHP_EOL;

$libgd->gdFree($png);
$libgd->gdImageDestroy($image);
```
