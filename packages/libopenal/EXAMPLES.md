# libopenal/libopenal examples

```php
use Pnlx\Libopenal\Libopenal;
use function Pnlx\Util\is_null;

// Open the default audio device and create a context
$device = Libopenal::alcOpenDevice(null);
if (is_null($device)) {
    echo "No audio device available\n";
} else {
    $ctx = Libopenal::alcCreateContext($device, null);
    Libopenal::alcMakeContextCurrent($ctx);

    // Query the renderer string (char* → PHP string)
    $renderer = Libopenal::alGetString(0xB004); // AL_RENDERER = 0xB004
    echo "OpenAL renderer: $renderer\n";

    Libopenal::alcMakeContextCurrent(null);
    Libopenal::alcDestroyContext($ctx);
    Libopenal::alcCloseDevice($device);
}
```
