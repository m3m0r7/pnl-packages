# libarchive Package

Package: `libarchive/libarchive`

Base library: libarchive

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libarchive
```

The package requires libarchive headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libarchive\Libarchive;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libarchive = $runtime->load(Libarchive::class);

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

This snippet is printed when `pnl install libarchive` finishes — it comes from the package's `examples` field in `pnlx.json`.
