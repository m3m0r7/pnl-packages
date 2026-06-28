# libncurses/libncurses key and control-character names

Translate key codes and control characters into their printable names without opening a terminal screen.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libncurses\Libncurses;

// keyname() returns the symbolic name of a key code.
echo "keyname(65)=" . (string)Libncurses::keyname(65) . "\n";   // A
echo "keyname(263)=" . (string)Libncurses::keyname(263) . "\n"; // KEY_BACKSPACE

// unctrl() renders a control character in caret notation.
echo "unctrl(9)=" . (string)Libncurses::unctrl(9) . "\n"; // ^I
```
