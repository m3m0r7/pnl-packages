# libsdl/libsdl examples

```php
use Pnlx\Libsdl\Libsdl;
use function Pnlx\Util\is_null;

// Constants from the SDL headers are generated into @pnlx/.../const.php and live
// under the package namespace, so import them instead of redefining them.
// SDL_INIT_VIDEO is a #define, SDL_WINDOW_SHOWN an enum value, and
// SDL_WINDOWPOS_CENTERED a constant-argument macro (SDL_WINDOWPOS_CENTERED_DISPLAY(0))
// — all generated.
use const Pnlx\Libsdl\SDL_INIT_VIDEO;
use const Pnlx\Libsdl\SDL_WINDOW_SHOWN;
use const Pnlx\Libsdl\SDL_WINDOWPOS_CENTERED;

Libsdl::SDL_Init(SDL_INIT_VIDEO);
$window = Libsdl::SDL_CreateWindow('Hello', SDL_WINDOWPOS_CENTERED, SDL_WINDOWPOS_CENTERED, 640, 360, SDL_WINDOW_SHOWN);
if (is_null($window)) {
    throw new RuntimeException('SDL_CreateWindow failed: ' . Libsdl::SDL_GetError());
}
Libsdl::SDL_Delay(2000);
Libsdl::SDL_DestroyWindow($window);
Libsdl::SDL_Quit();
```
