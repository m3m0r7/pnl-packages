# libsndfile/libsndfile examples

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
