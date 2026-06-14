# libheif/libheif examples

```php
use Pnlx\Libheif\Libheif;
use function Pnlx\Util\is_null;

// Query libheif version string
$version = Libheif::heif_get_version();
echo "libheif version: " . $version . "\n";

// Allocate a context, load a HEIF file, then release
$ctx = Libheif::heif_context_alloc();
if (!is_null($ctx)) {
    // $err = Libheif::heif_context_read_from_file($ctx, 'image.heic', null);
    Libheif::heif_context_free($ctx);
}
```
