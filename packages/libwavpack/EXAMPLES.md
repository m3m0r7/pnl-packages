# libwavpack/libwavpack examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libwavpack\Libwavpack;

// WavpackGetLibraryVersionString() returns the library version, e.g. "5.7.0".
$version = Libwavpack::WavpackGetLibraryVersionString();
echo "WavPack version: $version\n";

// Explore further: WavpackOpenFileInput(), WavpackUnpackSamples(),
// WavpackGetNumSamples(), WavpackGetSampleRate(), ...
```
