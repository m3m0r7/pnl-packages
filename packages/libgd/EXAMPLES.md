# libgd/libgd examples

```php
use Pnlx\Libgd\Libgd;
use function Pnlx\Util\is_null;

// Create a 200x100 true-colour image, draw a filled red rectangle, save as PNG.
$image = Libgd::gdImageCreateTrueColor(200, 100);
if (is_null($image)) {
    throw new \RuntimeException('gdImageCreateTrueColor() failed');
}

$red  = Libgd::gdImageColorAllocate($image, 255, 0, 0);
Libgd::gdImageFilledRectangle($image, 0, 0, 199, 99, $red);

// gdImagePngPtr(image, int *size) writes the blob length into its out-parameter.
$size = 0;
$png = Libgd::gdImagePngPtr($image, $size);
echo "PNG blob: {$size} bytes" . PHP_EOL;

Libgd::gdFree($png);
Libgd::gdImageDestroy($image);
```
