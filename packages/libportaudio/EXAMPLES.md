# libportaudio/libportaudio examples

```php
use Pnlx\Libportaudio\Libportaudio;

// Initialise PortAudio and print library version info
$err = Libportaudio::Pa_Initialize();
if ($err !== 0) { // paNoError = 0
    throw new \RuntimeException('Pa_Initialize failed: ' . Libportaudio::Pa_GetErrorText($err));
}

$versionText = Libportaudio::Pa_GetVersionText();
echo "PortAudio: {$versionText}\n";

$deviceCount = Libportaudio::Pa_GetDeviceCount();
echo "Audio devices: {$deviceCount}\n";

// Open a default output stream: Libportaudio::Pa_OpenDefaultStream($stream, 0, 2, paFloat32, 44100, 256, $callback, null)
Libportaudio::Pa_Terminate();
```
