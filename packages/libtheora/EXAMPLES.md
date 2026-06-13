# libtheora/libtheora examples

```php
use Pnlx\Libtheora\Libtheora;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libtheora = $runtime->load(Libtheora::class);

// th_version_string() returns the Theora release string.
$version = $libtheora->th_version_string();
echo "libtheora: $version\n";

// Explore further: th_decode_alloc(), th_decode_packetin(),
// th_encode_alloc(), th_encode_packetout(), ...
```
