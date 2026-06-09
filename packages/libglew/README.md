# GLEW Package

Package: `libglew/libglew`

Base library: GLEW

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libglew
```

The package requires GLEW headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libglew\Libglew;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libglew = $runtime->load(Libglew::class);

// glewGetString returns a GLubyte* (string) with GLEW version info.
// A valid OpenGL context must be current before calling glewInit().
$versionStr = $libglew->glewGetString(1); // GLEW_VERSION = 1
echo "GLEW version: " . $versionStr . "\n";

// After glewInit() succeeds (rc == GLEW_OK == 0), extension checks become available.
// $rc = $libglew->glewInit();
// $supported = $libglew->glewIsSupported('GL_ARB_vertex_array_object');
```

This snippet is printed when `pnl install libglew` finishes — it comes from the package's `examples` field in `pnlx.json`.
