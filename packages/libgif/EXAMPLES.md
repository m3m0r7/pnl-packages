# libgif/libgif examples

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
