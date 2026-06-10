# libportaudio/libportaudio examples

```php
use Pnlx\Libportaudio\Libportaudio;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libportaudio = $runtime->load(Libportaudio::class);

// Initialise PortAudio and print library version info
$err = $libportaudio->Pa_Initialize();
if ($err !== 0) { // paNoError = 0
    throw new \RuntimeException('Pa_Initialize failed: ' . $libportaudio->Pa_GetErrorText($err));
}

$versionText = $libportaudio->Pa_GetVersionText();
echo "PortAudio: {$versionText}\n";

$deviceCount = $libportaudio->Pa_GetDeviceCount();
echo "Audio devices: {$deviceCount}\n";

// Open a default output stream: $libportaudio->Pa_OpenDefaultStream($stream, 0, 2, paFloat32, 44100, 256, $callback, null)
$libportaudio->Pa_Terminate();
```
