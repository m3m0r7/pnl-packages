# libassimp texture types

Map values of the `aiTextureType` enum to their human-readable names with `aiTextureTypeToString()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libassimp\Libassimp;
use Pnlx\Libassimp\Enums\aiTextureType;

// Map a few aiTextureType enum values to their human-readable names.
foreach ([
    aiTextureType::aiTextureType_DIFFUSE,
    aiTextureType::aiTextureType_NORMALS,
    aiTextureType::aiTextureType_METALNESS,
    aiTextureType::aiTextureType_EMISSION_COLOR,
] as $type) {
    $name = Libassimp::aiTextureTypeToString($type);
    echo $type->name . ' => ' . (string)$name . "\n";
}
```
