# libopenjp2/libopenjp2 examples

```php
use Pnlx\Libopenjp2\Libopenjp2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libopenjp2 = $runtime->load(Libopenjp2::class);

// opj_version() returns the OpenJPEG version string, e.g. "2.5.2".
$version = $libopenjp2->opj_version();
echo "OpenJPEG: $version\n";

// Explore further: opj_create_decompress(), opj_setup_decoder(),
// opj_read_header(), opj_decode(), ...
```
