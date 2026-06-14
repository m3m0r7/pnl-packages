# libmagic/libmagic examples

```php
use Pnlx\Libmagic\Libmagic;
use function Pnlx\Util\is_null;

$libmagic = new Libmagic();

// Detect the MIME type of a file using libmagic.
$magic = $libmagic->magic_open(0x000010); // MAGIC_MIME_TYPE = 0x000010
if (is_null($magic)) {
    throw new \RuntimeException('magic_open failed');
}
$libmagic->magic_load($magic, null); // null = use default magic database
$mimeType = $libmagic->magic_file($magic, '/etc/hosts'); // returns string
echo $mimeType . PHP_EOL; // e.g. "text/plain"
$libmagic->magic_close($magic);
```
