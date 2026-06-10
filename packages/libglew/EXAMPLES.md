# libglew/libglew examples

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
