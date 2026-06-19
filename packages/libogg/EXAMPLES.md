# libogg/libogg examples

```php
use Pnlx\Libogg\Libogg;
use Pnlx\Libogg\Types\ogg_sync_state;

// Allocate an ogg_sync_state, initialise it, then release it.
$oy = new ogg_sync_state();
Libogg::ogg_sync_init($oy);           // returns 0 on success
$buffer = Libogg::ogg_sync_buffer($oy, 4096); // hands back a writable buffer pointer
echo $buffer !== null ? "ogg_sync initialised\n" : "failed\n";
Libogg::ogg_sync_clear($oy);
```
