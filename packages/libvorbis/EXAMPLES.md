# libvorbis/libvorbis examples

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
