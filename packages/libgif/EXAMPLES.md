# libgif/libgif examples

```php
use Pnlx\Libgif\Libgif;
use function Pnlx\Util\is_null;

// Open a GIF file for reading (returns GifFileType* handle)
$error = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$gif = Libgif::DGifOpenFileName('animation.gif', $error);
if (is_null($gif)) {
    echo "Could not open GIF (error code: " . $error[0] . ")\n";
} else {
    Libgif::DGifSlurp($gif);
    echo "Image count: " . $gif->ImageCount . "\n";
    Libgif::DGifCloseFile($gif, $error);
}
```
