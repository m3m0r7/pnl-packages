# libzip Package

Package: `libzip/libzip`

Base library: libzip

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libzip
```

The package requires libzip headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libzip\Libzip;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libzip = $runtime->load(Libzip::class);

// zip_open() opens a ZIP archive; zip_get_num_entries() counts its entries.
$errp = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$zip = $libzip->zip_open("/path/to/archive.zip", 0, $errp);
if (is_null($zip)) {
    echo "zip_open failed, error: " . $errp[0] . "\n";
} else {
    $count = $libzip->zip_get_num_entries($zip, 0);
    echo "Entries: $count\n";
    $libzip->zip_close($zip);
}
```

This snippet is printed when `pnl install libzip` finishes — it comes from the package's `examples` field in `pnlx.json`.
