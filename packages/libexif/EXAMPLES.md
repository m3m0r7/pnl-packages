# libexif/libexif examples

```php
use Pnlx\Libexif\Libexif;
use function Pnlx\Util\is_null;

$libexif = new Libexif();

// Load EXIF data from a JPEG file.
$data = $libexif->exif_data_new_from_file('/path/to/photo.jpg');
if (is_null($data)) {
    echo "No EXIF data found." . PHP_EOL;
} else {
    // Dump all tags to stdout (uses the library's own formatter).
    $libexif->exif_data_dump($data);
    $libexif->exif_data_unref($data);
}

// exif_data_new_from_data() can parse raw bytes from a variable instead.
```
