# libmagic/libmagic examples

```php
use Pnlx\Libmagic\Libmagic;
use function Pnlx\Util\is_null;

// Detect the MIME type of a file using libmagic.
$magic = Libmagic::magic_open(0x000010); // MAGIC_MIME_TYPE = 0x000010
if (is_null($magic)) {
    throw new \RuntimeException('magic_open failed');
}
Libmagic::magic_load($magic, null); // null = use default magic database
$mimeType = Libmagic::magic_file($magic, '/etc/hosts'); // returns string
echo $mimeType . PHP_EOL; // e.g. "text/plain"
Libmagic::magic_close($magic);
```
