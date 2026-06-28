# libportaudio version and sample sizes

`Pa_GetVersion()` and `Pa_GetSampleSize()` are pure queries that work without calling `Pa_Initialize()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libportaudio\Libportaudio;

// Pa_GetVersion() returns the numeric build version (no Pa_Initialize required).
$version = Libportaudio::Pa_GetVersion();
$version = is_object($version) ? $version->toInt() : $version;
echo "PortAudio build: {$version}\n";

// Pa_GetSampleSize() reports the byte width of a sample format (paInt16 = 8).
$size = Libportaudio::Pa_GetSampleSize(8);
$size = is_object($size) ? $size->toInt() : $size;
echo "paInt16 sample size: {$size} bytes\n";
```
