# libsdl/libsdl examples

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
