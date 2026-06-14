# libevent/libevent examples

```php
use Pnlx\Libevent\Libevent;
use function Pnlx\Util\is_null;

// Query the libevent version string and method (backend) name.
$version = Libevent::event_get_version();
echo "libevent version: " . $version . PHP_EOL;

// Create a default event_base (uses best available backend).
$base = Libevent::event_base_new();
if (is_null($base)) {
    throw new \RuntimeException('event_base_new() failed');
}
$method = Libevent::event_base_get_method($base);
echo "Backend method: " . $method . PHP_EOL;

Libevent::event_base_free($base);
```
