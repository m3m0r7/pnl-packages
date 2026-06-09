# Vorbis Package

Package: `libvorbis/libvorbis`

Base library: Vorbis

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libvorbis
```

The package requires Vorbis headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libvorbis\Libvorbis;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libvorbis = $runtime->load(Libvorbis::class);

// vorbis_version_string() returns the library version as a plain C string.
$version = $libvorbis->vorbis_version_string();
echo "Vorbis version: $version\n";

// Explore further: vorbis_info_init(), vorbis_encode_init(),
// vorbis_analysis_init(), vorbis_block_init(), vorbis_analysis_wrote(), ...
```

This snippet is printed when `pnl install libvorbis` finishes — it comes from the package's `examples` field in `pnlx.json`.
