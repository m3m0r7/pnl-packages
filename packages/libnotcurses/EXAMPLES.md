# libnotcurses/libnotcurses examples

```php
use Pnlx\Libnotcurses\Libnotcurses;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnotcurses = $runtime->load(Libnotcurses::class);

// notcurses_version() returns the runtime version, e.g. "3.0.9".
$version = $libnotcurses->notcurses_version();
echo "notcurses: $version\n";

// Explore further: notcurses_core_init(), notcurses_stdplane(),
// ncplane_putstr(), notcurses_render(), notcurses_stop(), ...
```
