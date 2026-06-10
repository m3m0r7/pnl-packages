# libevent/libevent examples

```php
use Pnlx\Libevent\Libevent;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libevent = $runtime->load(Libevent::class);

// Query the libevent version string and method (backend) name.
$version = $libevent->event_get_version();
echo "libevent version: " . $version . PHP_EOL;

// Create a default event_base (uses best available backend).
$base = $libevent->event_base_new();
if (is_null($base)) {
    throw new \RuntimeException('event_base_new() failed');
}
$method = $libevent->event_base_get_method($base);
echo "Backend method: " . $method . PHP_EOL;

$libevent->event_base_free($base);
```
