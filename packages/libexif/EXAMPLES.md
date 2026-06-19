# libexif/libexif examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libexif\Libexif;
use function Pnlx\Util\is_null;

// Load EXIF data from a JPEG file.
$data = Libexif::exif_data_new_from_file('/path/to/photo.jpg');
if (is_null($data)) {
    echo "No EXIF data found." . PHP_EOL;
} else {
    // Dump all tags to stdout (uses the library's own formatter).
    Libexif::exif_data_dump($data);
    Libexif::exif_data_unref($data);
}

// exif_data_new_from_data() can parse raw bytes from a variable instead.
```
