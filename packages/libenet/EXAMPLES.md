# libenet/libenet examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libenet\Libenet;

// enet_initialize() must be called once before any other ENet call.
if (Libenet::enet_initialize()->toInt() !== 0) {
    throw new \RuntimeException('ENet failed to initialise');
}

// enet_linked_version() returns the runtime ENetVersion.
$version = Libenet::enet_linked_version();
echo "ENet version code: $version\n";
Libenet::enet_deinitialize();

// Explore further: enet_host_create(), enet_host_connect(),
// enet_host_service(), enet_packet_create(), ...
```
