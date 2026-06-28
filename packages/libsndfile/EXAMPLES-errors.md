# libsndfile error descriptions

Translate libsndfile error codes into human-readable descriptions with `sf_error_number()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsndfile\Libsndfile;

// Map libsndfile error codes to their human-readable descriptions.
for ($code = 0; $code <= 4; $code++) {
    $message = Libsndfile::sf_error_number($code);
    echo $code . ': ' . (string) $message . PHP_EOL;
}
```
