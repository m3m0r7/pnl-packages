# libglew error string lookup

Translate a GLEW initialization error code into a human-readable message with `glewGetErrorString`, which needs no current OpenGL context.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libglew\Libglew;

// glewGetErrorString maps a GLEW init error code to a message (no GL context needed).
foreach ([0, 1, 2, 3] as $code) {
    $msg = Libglew::glewGetErrorString($code);
    echo "glew error {$code}: " . ((string)$msg) . "\n";
}
```
