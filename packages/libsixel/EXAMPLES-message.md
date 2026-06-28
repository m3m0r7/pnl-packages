# libsixel/libsixel additional diagnostic message

Set and read back libsixel's thread-local "additional message" buffer that helpers use to explain failures.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsixel\Libsixel;

// libsixel keeps a thread-local "additional message" buffer that helpers append to
// when they need to explain a failure in more detail than a status code allows.
// You can drive it directly: set a diagnostic string, then read it back. Both calls
// take/return plain strings (the getter's String_ wrapper casts cleanly).
echo 'Initial additional message: [' . (string) Libsixel::sixel_helper_get_additional_message() . "]\n";

Libsixel::sixel_helper_set_additional_message('failed to open /tmp/missing.png');
echo 'After set: [' . (string) Libsixel::sixel_helper_get_additional_message() . "]\n";
```
