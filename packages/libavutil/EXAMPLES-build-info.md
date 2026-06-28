# libavutil build information

Read the build version string, configure flags, and license of the linked libavutil.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libavutil\Libavutil;

// Human-readable build version string.
echo "version info: " . (string) Libavutil::av_version_info() . "\n";

// The configure flags FFmpeg/libavutil was built with.
echo "configuration: " . (string) Libavutil::avutil_configuration() . "\n";

// The license under which this libavutil build is distributed.
echo "license: " . (string) Libavutil::avutil_license() . "\n";
```
