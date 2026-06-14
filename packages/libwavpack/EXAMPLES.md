# libwavpack/libwavpack examples

```php
use Pnlx\Libwavpack\Libwavpack;

$libwavpack = new Libwavpack();

// WavpackGetLibraryVersionString() returns the library version, e.g. "5.7.0".
$version = $libwavpack->WavpackGetLibraryVersionString();
echo "WavPack version: $version\n";

// Explore further: WavpackOpenFileInput(), WavpackUnpackSamples(),
// WavpackGetNumSamples(), WavpackGetSampleRate(), ...
```
