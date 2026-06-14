# libenet/libenet examples

```php
use Pnlx\Libenet\Libenet;

$libenet = new Libenet();

// enet_initialize() must be called once before any other ENet call.
if ($libenet->enet_initialize() !== 0) {
    throw new \RuntimeException('ENet failed to initialise');
}

// enet_linked_version() returns the runtime ENetVersion.
$version = $libenet->enet_linked_version();
echo "ENet version code: $version\n";
$libenet->enet_deinitialize();

// Explore further: enet_host_create(), enet_host_connect(),
// enet_host_service(), enet_packet_create(), ...
```
