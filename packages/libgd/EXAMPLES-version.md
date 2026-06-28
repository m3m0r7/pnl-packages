# libgd version information

Report the linked GD library version both as a string and as its numeric major/minor/release components.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgd\Libgd;

// gdVersionString() returns the full GD version as a string.
echo "GD version: " . (string)Libgd::gdVersionString() . PHP_EOL;

// gdMajorVersion() / gdMinorVersion() / gdReleaseVersion() return the numeric components.
$major = Libgd::gdMajorVersion();
$minor = Libgd::gdMinorVersion();
$release = Libgd::gdReleaseVersion();
printf(
    "components: %d.%d.%d" . PHP_EOL,
    is_object($major) ? $major->toInt() : $major,
    is_object($minor) ? $minor->toInt() : $minor,
    is_object($release) ? $release->toInt() : $release
);
```
