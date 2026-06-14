# libopenal/libopenal examples

```php
use Pnlx\Libopenal\Libopenal;
use function Pnlx\Util\is_null;

$libopenal = new Libopenal();

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
