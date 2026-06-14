# libgif/libgif examples

```php
use Pnlx\Libgif\Libgif;
use function Pnlx\Util\is_null;

$libgif = new Libgif();

// Open a GIF file for reading (returns GifFileType* handle)
$error = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$gif = $libgif->DGifOpenFileName('animation.gif', $error);
if (is_null($gif)) {
    echo "Could not open GIF (error code: " . $error[0] . ")\n";
} else {
    $libgif->DGifSlurp($gif);
    echo "Image count: " . $gif->ImageCount . "\n";
    $libgif->DGifCloseFile($gif, $error);
}
```
