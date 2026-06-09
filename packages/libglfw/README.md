# GLFW Package

Package: `libglfw/libglfw`

Base library: GLFW

License: Zlib

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libglfw
```

The package requires GLFW headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libglfw\Libglfw;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libglfw = $runtime->load(Libglfw::class);

// Query GLFW version string before initializing (always safe)
$versionStr = $libglfw->glfwGetVersionString();
echo "GLFW: " . $versionStr . "\n";

// Initialize GLFW, create a window, then terminate
if ($libglfw->glfwInit()) {
    $libglfw->glfwWindowHint(0x00022001, 1); // GLFW_CONTEXT_VERSION_MAJOR = 3
    // $window = $libglfw->glfwCreateWindow(800, 600, 'Hello', null, null);
    $libglfw->glfwTerminate();
}
```

This snippet is printed when `pnl install libglfw` finishes — it comes from the package's `examples` field in `pnlx.json`.
