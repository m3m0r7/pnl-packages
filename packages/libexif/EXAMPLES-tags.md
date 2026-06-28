# libexif/libexif tag-lookup examples

Resolve an EXIF tag id from its name and map it back to a name/title, plus look up a byte-order constant's name.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libexif\Libexif;

// Resolve an EXIF tag id from its canonical name, then map it back.
$tag = Libexif::exif_tag_from_name('Model');
$tag = is_object($tag) ? $tag->toInt() : $tag;
echo "tag id for 'Model': " . $tag . PHP_EOL;
echo "name:  " . (string)Libexif::exif_tag_get_name($tag) . PHP_EOL;
echo "title: " . (string)Libexif::exif_tag_get_title($tag) . PHP_EOL;

// Human-readable name for a byte-order constant (0 = Motorola/big-endian).
echo "byte order 0: " . (string)Libexif::exif_byte_order_get_name(0) . PHP_EOL;
```
