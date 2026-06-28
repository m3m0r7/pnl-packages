# libvpx/libvpx error strings and numeric version

Decode a `vpx_codec_err_t` value into its human-readable message and read the packed numeric library version.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libvpx\Libvpx;

// vpx_codec_version() returns the packed numeric version (major<<16 | minor<<8 | patch).
$v = Libvpx::vpx_codec_version();
$v = is_object($v) ? $v->toInt() : $v;
echo 'numeric version: ', $v, ' (', ($v >> 16), '.', (($v >> 8) & 0xff), '.', ($v & 0xff), ")\n";

// vpx_codec_version_extra_str() returns any extra version suffix (often empty).
$extra = Libvpx::vpx_codec_version_extra_str();
echo 'extra version: "', (string) $extra, "\"\n";

// vpx_codec_err_to_string(int) maps an error code to its human-readable name.
echo 'err 0: ', (string) Libvpx::vpx_codec_err_to_string(0), "\n"; // Success
echo 'err 8: ', (string) Libvpx::vpx_codec_err_to_string(8), "\n"; // Invalid parameter
```
