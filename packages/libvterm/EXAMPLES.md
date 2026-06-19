# libvterm/libvterm examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libvterm\Libvterm;

// Create an 80x24 virtual terminal, then free it.
$vt = Libvterm::vterm_new(24, 80);
Libvterm::vterm_free($vt);

// Explore further: vterm_obtain_screen(), vterm_input_write(),
// vterm_screen_get_cell(), vterm_screen_reset(), ...
```
