# OpenAL Soft Package

Package: `libopenal/libopenal`

Base library: OpenAL Soft

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libopenal
```

The package requires OpenAL Soft headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libopenal\Libopenal;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libopenal = $runtime->load(Libopenal::class);

// Open the default audio device and create a context
$device = $libopenal->alcOpenDevice(null);
if (is_null($device)) {
    echo "No audio device available\n";
} else {
    $ctx = $libopenal->alcCreateContext($device, null);
    $libopenal->alcMakeContextCurrent($ctx);

    // Query the renderer string (char* → PHP string)
    $renderer = $libopenal->alGetString(0xB004); // AL_RENDERER = 0xB004
    echo "OpenAL renderer: $renderer\n";

    $libopenal->alcMakeContextCurrent(null);
    $libopenal->alcDestroyContext($ctx);
    $libopenal->alcCloseDevice($device);
}
```

This snippet is printed when `pnl install libopenal` finishes — it comes from the package's `examples` field in `pnlx.json`.
