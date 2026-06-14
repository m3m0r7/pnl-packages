# libarchive/libarchive examples

```php
use Pnlx\Libarchive\Libarchive;
use function Pnlx\Util\is_null;

$libarchive = new Libarchive();

// Read a tar.gz archive entry by entry
$a = $libarchive->archive_read_new();
if (is_null($a)) {
    throw new \RuntimeException('archive_read_new failed');
}
$libarchive->archive_read_support_filter_gzip($a);
$libarchive->archive_read_support_format_tar($a);
$libarchive->archive_read_open_filename($a, 'archive.tar.gz', 10240);
// Process entries: $libarchive->archive_read_next_header($a, $entry)
$libarchive->archive_read_free($a);
```
