# libgif/libgif examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgif\Libgif;
use function Pnlx\Util\is_null;

// Open a GIF file for reading (returns GifFileType* handle). The int error code
// is an out-parameter: pass a plain variable by reference.
$error = 0;
$gif = Libgif::DGifOpenFileName('animation.gif', $error);
if (is_null($gif)) {
    echo "Could not open GIF (error code: {$error})\n";
} else {
    Libgif::DGifSlurp($gif);
    echo "Image count: " . $gif->cdata()->ImageCount . "\n";
    Libgif::DGifCloseFile($gif, $error);
}
```
