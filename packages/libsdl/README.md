# SDL Package

Package: `libsdl/libsdl`

Base library: SDL2

License: Zlib

Install with `pnl`:

```sh
pnl install libsdl
```

The package requires SDL2 headers and library files.

## PHP usage

SDL is called statically — a C library is just a bag of functions, and the first
static call boots the extension. Constants from the SDL headers are generated
under the package namespace, so import them instead of redefining them.

A window only paints once a **renderer** is bound to it; without one the window
stays blank, and on macOS it may not even appear. This example draws "Hello
World!" with a tiny bitmap font (SDL itself has no text renderer — that's
SDL_ttf) and pumps the OS event queue so the window actually shows:

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsdl\Libsdl;
use function Pnlx\Util\is_null;

use const Pnlx\Libsdl\SDL_INIT_VIDEO;
use const Pnlx\Libsdl\SDL_WINDOW_SHOWN;
use const Pnlx\Libsdl\SDL_WINDOWPOS_CENTERED;

// 5x7 bitmap font for "Hello World!"; '1' marks a lit pixel (7 rows per glyph).
$font = [
    'H' => ['10001', '10001', '10001', '11111', '10001', '10001', '10001'],
    'e' => ['00000', '00000', '01110', '10001', '11111', '10000', '01110'],
    'l' => ['01100', '00100', '00100', '00100', '00100', '00100', '01110'],
    'o' => ['00000', '00000', '01110', '10001', '10001', '10001', '01110'],
    'W' => ['10001', '10001', '10001', '10101', '10101', '11011', '10001'],
    'r' => ['00000', '00000', '10110', '11001', '10000', '10000', '10000'],
    'd' => ['00001', '00001', '01101', '10011', '10001', '10001', '01111'],
    '!' => ['00100', '00100', '00100', '00100', '00100', '00000', '00100'],
    ' ' => ['00000', '00000', '00000', '00000', '00000', '00000', '00000'],
];

if (Libsdl::SDL_Init(SDL_INIT_VIDEO)->toInt() !== 0) {
    throw new RuntimeException('SDL_Init failed: ' . Libsdl::SDL_GetError());
}

$window = Libsdl::SDL_CreateWindow('Hello World!', SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 640, 360, SDL_WINDOW_SHOWN);
if (is_null($window)) {
    throw new RuntimeException('SDL_CreateWindow failed: ' . Libsdl::SDL_GetError());
}

$renderer = Libsdl::SDL_CreateRenderer($window, -1, 0);
if (is_null($renderer)) {
    throw new RuntimeException('SDL_CreateRenderer failed: ' . Libsdl::SDL_GetError());
}

Libsdl::SDL_SetRenderDrawColor($renderer, 0x1E, 0x1E, 0x1E, 0xFF);
Libsdl::SDL_RenderClear($renderer);

Libsdl::SDL_SetRenderDrawColor($renderer, 0xFF, 0xFF, 0xFF, 0xFF);
$scale = 6;
$x = 70;
$y = 150;
foreach (str_split('Hello World!') as $char) {
    $glyph = $font[$char] ?? $font[' '];
    foreach ($glyph as $row => $bits) {
        for ($col = 0; $col < 5; $col++) {
            if ($bits[$col] !== '1') {
                continue;
            }
            for ($dy = 0; $dy < $scale; $dy++) {
                for ($dx = 0; $dx < $scale; $dx++) {
                    Libsdl::SDL_RenderDrawPoint($renderer, $x + $col * $scale + $dx, $y + $row * $scale + $dy);
                }
            }
        }
    }
    $x += 6 * $scale; // 5px glyph + 1px gap
}

Libsdl::SDL_RenderPresent($renderer);
$until = microtime(true) + 3.0;
while (microtime(true) < $until) {
    Libsdl::SDL_PumpEvents();
    Libsdl::SDL_Delay(16);
}

Libsdl::SDL_DestroyRenderer($renderer);
Libsdl::SDL_DestroyWindow($window);
Libsdl::SDL_Quit();
```

### Native info dialog (no window needed)

The simplest visible call is a native message box — no window, renderer or event
loop. `SDL_ShowSimpleMessageBox` blocks until the user clicks OK, so it works as
a one-call "alert"/info popup. This is the snippet printed when `pnl install
libsdl` finishes — it comes from the package's `examples` field (`EXAMPLES.md`):

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsdl\Libsdl;

use const Pnlx\Libsdl\SDL_INIT_VIDEO;
use const Pnlx\Libsdl\SDL_MESSAGEBOX_INFORMATION;

if (Libsdl::SDL_Init(SDL_INIT_VIDEO)->toInt() !== 0) {
    throw new RuntimeException('SDL_Init failed: ' . Libsdl::SDL_GetError());
}

// flags, title, message, parent window (null = standalone dialog).
Libsdl::SDL_ShowSimpleMessageBox(SDL_MESSAGEBOX_INFORMATION, 'pnl + SDL', 'Hello World!', null);

Libsdl::SDL_Quit();
```
