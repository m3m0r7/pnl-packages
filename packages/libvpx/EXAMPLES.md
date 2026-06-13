# libvpx/libvpx examples

```php
use Pnlx\Libvpx\Libvpx;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libvpx = $runtime->load(Libvpx::class);

// vpx_codec_version_str() returns the library version, e.g. "v1.14.1".
$version = $libvpx->vpx_codec_version_str();
echo "libvpx version: $version\n";

// vpx_codec_build_config() reports the compile-time configuration.
echo $libvpx->vpx_codec_build_config(), "\n";

// Explore further: vpx_codec_enc_init(), vpx_codec_encode(),
// vpx_codec_decode(), vpx_codec_get_frame(), ...
```
