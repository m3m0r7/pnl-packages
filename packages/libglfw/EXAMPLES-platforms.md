# libglfw platform backend probe

Use `glfwPlatformSupported` to ask which windowing backends GLFW was compiled with; it is safe to call before `glfwInit`, so no display or GL context is required.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libglfw\Libglfw;

// glfwPlatformSupported reports compile-time platform backends; safe before glfwInit.
$platforms = [
    'COCOA'   => 0x00060002,
    'WIN32'   => 0x00060001,
    'WAYLAND' => 0x00060003,
    'X11'     => 0x00060004,
    'NULL'    => 0x00060005,
];
foreach ($platforms as $name => $id) {
    $rc = Libglfw::glfwPlatformSupported($id);
    $rc = is_object($rc) ? $rc->toInt() : $rc;
    echo "{$name}: " . ($rc ? 'supported' : 'no') . "\n";
}
```
