# libargon2/libargon2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libargon2\Libargon2;

// argon2_type2string maps an argon2 type id to its name (0=Argon2d, 1=Argon2i, 2=Argon2id).
echo Libargon2::argon2_type2string(1, 1) . "\n"; // Argon2i
```
