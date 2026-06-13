# libvterm/libvterm examples

```php
use Pnlx\Libvterm\Libvterm;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libvterm = $runtime->load(Libvterm::class);

// Create an 80x24 virtual terminal, then free it.
$vt = $libvterm->vterm_new(24, 80);
$libvterm->vterm_free($vt);

// Explore further: vterm_obtain_screen(), vterm_input_write(),
// vterm_screen_get_cell(), vterm_screen_reset(), ...
```
