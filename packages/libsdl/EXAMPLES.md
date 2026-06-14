# libsdl/libsdl examples

```php
use Pnlx\Libsdl\Libsdl;
use function Pnlx\Util\is_null;

// Constants from the SDL headers are generated into @pnlx/.../const.php and
// live under the package namespace, so import them instead of redefining them.
// SDL_INIT_VIDEO is a #define; SDL_WINDOW_SHOWN is an enum value — both generated.
use const Pnlx\Libsdl\SDL_INIT_VIDEO;
use const Pnlx\Libsdl\SDL_WINDOW_SHOWN;

// SDL_WINDOWPOS_CENTERED is a function-like macro (SDL_WINDOWPOS_CENTERED_DISPLAY(0)),
// so it cannot be generated as a constant — define it by hand.
const SDL_WINDOWPOS_CENTERED = 0x2FFF0000;

$sdl = new Libsdl();

$sdl->SDL_Init(SDL_INIT_VIDEO);
$window = $sdl->SDL_CreateWindow('Hello', SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 640, 360, SDL_WINDOW_SHOWN);
if (is_null($window)) {
    throw new RuntimeException('SDL_CreateWindow failed: ' . $sdl->SDL_GetError());
}
$sdl->SDL_Delay(2000);
$sdl->SDL_DestroyWindow($window);
$sdl->SDL_Quit();
```
