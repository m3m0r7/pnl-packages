# libsndfile/libsndfile examples

```php
use Pnlx\Libsndfile\Libsndfile;
use function Pnlx\Util\is_null;

$libsndfile = new Libsndfile();

// Get the libsndfile version string.
$version = $libsndfile->sf_version_string();
echo $version . PHP_EOL;

// Open a sound file (read-only). SF_INFO must be allocated as a struct.
// $info = ...; // allocate SF_INFO via (new \Pnlx\FFI\Allocator())
// $sndfile = $libsndfile->sf_open('/path/to/audio.wav', 0x10 /* SFM_READ */, $info);
// if (!is_null($sndfile)) { $libsndfile->sf_close($sndfile); }
```
