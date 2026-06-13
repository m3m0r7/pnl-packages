# libwavpack/libwavpack examples

```php
use Pnlx\Libwavpack\Libwavpack;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libwavpack = $runtime->load(Libwavpack::class);

// WavpackGetLibraryVersionString() returns the library version, e.g. "5.7.0".
$version = $libwavpack->WavpackGetLibraryVersionString();
echo "WavPack version: $version\n";

// Explore further: WavpackOpenFileInput(), WavpackUnpackSamples(),
// WavpackGetNumSamples(), WavpackGetSampleRate(), ...
```
