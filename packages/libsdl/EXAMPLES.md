# libsdl/libsdl examples

A minimal, display-free SDL session: initialise the video subsystem and ask SDL
which video driver it picked. On a headless host set `SDL_VIDEODRIVER=dummy` and
SDL initialises without an X11/Wayland server, so this runs anywhere (CI included)
without opening a window.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsdl\Libsdl;

// A C library is a bag of functions, so SDL is called statically (no
// instantiation); the first static call boots the extension.
use const Pnlx\Libsdl\SDL_INIT_VIDEO;

if (Libsdl::SDL_Init(SDL_INIT_VIDEO)->toInt() !== 0) {
    throw new RuntimeException('SDL_Init failed: ' . Libsdl::SDL_GetError());
}

// The active video driver — "dummy" on a headless host (SDL_VIDEODRIVER=dummy),
// or e.g. "x11"/"cocoa"/"windows" on a desktop. A `const char *` return arrives
// as a PHP string.
$driver = Libsdl::SDL_GetCurrentVideoDriver();
echo 'SDL initialised; video driver: ', $driver, PHP_EOL;

Libsdl::SDL_Quit();
```

For a graphical "Hello World!" message box on a desktop with a display, call
`SDL_ShowSimpleMessageBox(SDL_MESSAGEBOX_INFORMATION, 'pnl + SDL', 'Hello World!', null)`
after `SDL_Init` — it needs a real GUI, so it is not part of the headless example
above.
