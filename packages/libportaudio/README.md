# PortAudio Package

Package: `libportaudio/libportaudio`

Base library: PortAudio

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libportaudio
```

The package requires PortAudio headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libportaudio` finishes — it comes from the package's `examples` field in `pnlx.json`.
