# libglew/libglew examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libglew\Libglew;

// glewGetString returns a GLubyte* (string) with GLEW version info.
// A valid OpenGL context must be current before calling glewInit().
$versionStr = Libglew::glewGetString(1); // GLEW_VERSION = 1
echo "GLEW version: " . $versionStr . "\n";

// After glewInit() succeeds (rc == GLEW_OK == 0), extension checks become available.
// $rc = Libglew::glewInit();
// $supported = Libglew::glewIsSupported('GL_ARB_vertex_array_object');
```
