# libncurses/libncurses examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libncurses\Libncurses;

// curses_version() returns the library version without opening a terminal.
echo Libncurses::curses_version() . "\n"; // e.g. "ncurses 6.x"
```
