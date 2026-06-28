# libsdl/libsdl host-info example

Query SDL's static build and host information without `SDL_Init` or a display: the revision string, platform name, logical CPU count and total system RAM, so it runs anywhere including headless CI.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsdl\Libsdl;

// None of these need SDL_Init or a display: they report static build- and
// host-information, so they run anywhere (CI included).

// Exact SDL revision string this library was built from (a `const char *`).
$revision = Libsdl::SDL_GetRevision();
echo 'SDL revision: ', (string)$revision, PHP_EOL;

// The platform name SDL was compiled for, e.g. "Mac OS X", "Linux", "Windows".
$platform = Libsdl::SDL_GetPlatform();
echo 'Platform: ', (string)$platform, PHP_EOL;

// Number of logical CPU cores; an `int` arrives as a CData number wrapper.
$cores = Libsdl::SDL_GetCPUCount();
echo 'CPU cores: ', (is_object($cores) ? $cores->toInt() : $cores), PHP_EOL;

// Total system RAM in MiB.
$ram = Libsdl::SDL_GetSystemRAM();
echo 'System RAM (MiB): ', (is_object($ram) ? $ram->toInt() : $ram), PHP_EOL;
```
