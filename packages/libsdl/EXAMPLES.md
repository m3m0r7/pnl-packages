# libsdl/libsdl examples

The simplest thing SDL can show is a native message box — no window, renderer or
event loop required. `SDL_ShowSimpleMessageBox` blocks until the user clicks OK,
so it's a one-call "alert"/info popup.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsdl\Libsdl;

// A C library is a bag of functions, so SDL is called statically (no
// instantiation); the first static call boots the extension. SDL_MESSAGEBOX_INFORMATION
// is the "info" flavour (there are also _WARNING and _ERROR) — a generated enum
// value living under the package namespace, so import it instead of redefining it.
use const Pnlx\Libsdl\SDL_INIT_VIDEO;
use const Pnlx\Libsdl\SDL_MESSAGEBOX_INFORMATION;

if (Libsdl::SDL_Init(SDL_INIT_VIDEO)->toInt() !== 0) {
    throw new RuntimeException('SDL_Init failed: ' . Libsdl::SDL_GetError());
}

// flags, title, message, parent window (null = standalone dialog).
$result = Libsdl::SDL_ShowSimpleMessageBox(
    SDL_MESSAGEBOX_INFORMATION,
    'pnl + SDL',
    'Hello World!',
    null
);
if ($result->toInt() !== 0) {
    throw new RuntimeException('SDL_ShowSimpleMessageBox failed: ' . Libsdl::SDL_GetError());
}

Libsdl::SDL_Quit();
```
