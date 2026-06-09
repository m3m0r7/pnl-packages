# libidn2 Package

Package: `libidn2/libidn2`

Base library: libidn2

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libidn2
```

The package requires libidn2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libidn2\Libidn2;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libidn2 = $runtime->load(Libidn2::class);

// Check library version
$version = $libidn2->idn2_check_version('2.0.0');
echo "libidn2 version >= 2.0.0: " . ($version !== null ? $version : 'no') . "\n";

// Convert an internationalized domain name to ACE (ASCII-compatible encoding)
$output = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$rc = $libidn2->idn2_lookup_u8('www.bücher.example', $output, 0);
if ($rc === 0) {
    echo "ACE label: " . $output[0] . "\n";
    $libidn2->idn2_free($output[0]);
}
```

This snippet is printed when `pnl install libidn2` finishes — it comes from the package's `examples` field in `pnlx.json`.
