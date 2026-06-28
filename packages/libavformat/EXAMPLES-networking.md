# libavformat license and networking

Read the build's license string with `avformat_license()` and toggle the global networking layer with `avformat_network_init()` / `avformat_network_deinit()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libavformat\Libavformat;

// The license under which this libavformat build was compiled.
echo 'License: ' . (string)Libavformat::avformat_license() . "\n";

// Initialise the networking layer (needed for protocols like rtmp/http).
$init = Libavformat::avformat_network_init();
$init = is_object($init) ? $init->toInt() : $init;
echo 'avformat_network_init: ' . ($init === 0 ? 'ok' : "error ({$init})") . "\n";

// Tear the networking layer back down.
$deinit = Libavformat::avformat_network_deinit();
$deinit = is_object($deinit) ? $deinit->toInt() : $deinit;
echo 'avformat_network_deinit: ' . ($deinit === 0 ? 'ok' : "error ({$deinit})") . "\n";
```
