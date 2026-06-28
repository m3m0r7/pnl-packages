# libenet/libenet timing and RNG

Rebase and read ENet's millisecond timer with `enet_time_set()` / `enet_time_get()`, and obtain a platform-derived RNG seed with `enet_host_random_seed()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libenet\Libenet;

Libenet::enet_initialize();

// enet_time_set() rebases ENet's millisecond timer; enet_time_get() then
// reports the elapsed time since that base.
Libenet::enet_time_set(0);
$t = Libenet::enet_time_get();
echo 'ENet time (ms since base): ' . (is_object($t) ? $t->toInt() : $t) . PHP_EOL;

// enet_host_random_seed() returns a platform-derived seed for ENet's RNG.
$seed = Libenet::enet_host_random_seed();
echo 'ENet random seed is non-zero: ' . (((is_object($seed) ? $seed->toInt() : $seed) !== 0) ? 'yes' : 'no') . PHP_EOL;

Libenet::enet_deinitialize();
```
