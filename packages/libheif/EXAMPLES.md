# libheif/libheif examples

```php
use Pnlx\Libheif\Libheif;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libheif = $runtime->load(Libheif::class);

// Query libheif version string
$version = $libheif->heif_get_version();
echo "libheif version: " . $version . "\n";

// Allocate a context, load a HEIF file, then release
$ctx = $libheif->heif_context_alloc();
if (!is_null($ctx)) {
    // $err = $libheif->heif_context_read_from_file($ctx, 'image.heic', null);
    $libheif->heif_context_free($ctx);
}
```
