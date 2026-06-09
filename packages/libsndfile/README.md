# libsndfile Package

Package: `libsndfile/libsndfile`

Base library: libsndfile

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libsndfile
```

The package requires libsndfile headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libsndfile\Libsndfile;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libsndfile = $runtime->load(Libsndfile::class);

// Get the libsndfile version string.
$version = $libsndfile->sf_version_string();
echo $version . PHP_EOL;

// Open a sound file (read-only). SF_INFO must be allocated as a struct.
// $info = ...; // allocate SF_INFO via $runtime->allocator()
// $sndfile = $libsndfile->sf_open('/path/to/audio.wav', 0x10 /* SFM_READ */, $info);
// if (!is_null($sndfile)) { $libsndfile->sf_close($sndfile); }
```

This snippet is printed when `pnl install libsndfile` finishes — it comes from the package's `examples` field in `pnlx.json`.
