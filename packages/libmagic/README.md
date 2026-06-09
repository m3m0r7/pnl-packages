# libmagic Package

Package: `libmagic/libmagic`

Base library: libmagic

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmagic
```

The package requires libmagic headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmagic\Libmagic;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libmagic = $runtime->load(Libmagic::class);

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

This snippet is printed when `pnl install libmagic` finishes — it comes from the package's `examples` field in `pnlx.json`.
