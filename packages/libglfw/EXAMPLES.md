# libglfw/libglfw examples

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
