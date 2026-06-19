# libvpx/libvpx examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libvpx\Libvpx;

// vpx_codec_version_str() returns the library version, e.g. "v1.14.1".
$version = Libvpx::vpx_codec_version_str();
echo "libvpx version: $version\n";

// vpx_codec_build_config() reports the compile-time configuration.
echo Libvpx::vpx_codec_build_config(), "\n";

// Explore further: vpx_codec_enc_init(), vpx_codec_encode(),
// vpx_codec_decode(), vpx_codec_get_frame(), ...
```
