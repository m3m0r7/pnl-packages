# libapr/libapr version parts example

Fill an `apr_version_t` struct with `apr_version()` and read the numeric major/minor/patch fields.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libapr\Libapr;
use Pnlx\Libapr\Types\apr_version_t;

// apr_version() fills an apr_version_t struct with the numeric APR version parts.
$v = new apr_version_t();
Libapr::apr_version($v);
echo 'APR ' . $v->getMajor() . '.' . $v->getMinor() . '.' . $v->getPatch() . PHP_EOL;
```
