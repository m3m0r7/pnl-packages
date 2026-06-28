# libopenal/libopenal error state

Poll the AL and ALC error queues without opening a device — `alGetError` returns the AL-level error (`AL_INVALID_OPERATION` until a context is current) and `alcGetError(null)` returns the ALC error of the global/null device.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libopenal\Libopenal;

// AL error state (no current context yet → AL_INVALID_OPERATION = 0xA004 = 40964)
$alErr = Libopenal::alGetError();
echo 'AL error code: ' . (is_object($alErr) ? $alErr->toInt() : $alErr) . "\n";

// ALC error state of the null (global) device (ALC_NO_ERROR = 0)
$alcErr = Libopenal::alcGetError(null);
echo 'ALC error code: ' . (is_object($alcErr) ? $alcErr->toInt() : $alcErr) . "\n";
```
