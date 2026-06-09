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

```php
use Pnlx\Libsdl\Libsdl;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

const SDL_INIT_VIDEO = 0x00000020;
const SDL_WINDOWPOS_CENTERED = 0x2FFF0000;
const SDL_WINDOW_SHOWN = 0x00000004;

$runtime = new Runtime(__DIR__);
$sdl = $runtime->load(Libsdl::class);

$sdl->SDL_Init(SDL_INIT_VIDEO);
$window = $sdl->SDL_CreateWindow('Hello', SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 640, 360, SDL_WINDOW_SHOWN);
if (is_null($window)) {
    throw new RuntimeException('SDL_CreateWindow failed: ' . $sdl->SDL_GetError());
}
$sdl->SDL_Delay(2000);
$sdl->SDL_DestroyWindow($window);
$sdl->SDL_Quit();
```

This snippet is printed when `pnl install libsdl` finishes — it comes from the package's `examples` field. For a fuller example that draws "Hello World!" inside the window, see the renderer-based variants used in the project's `test2.php` / `test3.php`.
