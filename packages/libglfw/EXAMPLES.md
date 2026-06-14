# libglfw/libglfw examples

```php
use Pnlx\Libglfw\Libglfw;

// Query GLFW version string before initializing (always safe)
$versionStr = Libglfw::glfwGetVersionString();
echo "GLFW: " . $versionStr . "\n";

// Initialize GLFW, create a window, then terminate
if (Libglfw::glfwInit()) {
    Libglfw::glfwWindowHint(0x00022001, 1); // GLFW_CONTEXT_VERSION_MAJOR = 3
    // $window = Libglfw::glfwCreateWindow(800, 600, 'Hello', null, null);
    Libglfw::glfwTerminate();
}
```
