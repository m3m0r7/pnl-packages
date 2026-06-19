# libpq/libpq examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpq\Libpq;

// PQlibVersion() reports the client library version without connecting to a server.
$v = Libpq::PQlibVersion()->toInt();
printf("libpq %d.%d\n", intdiv($v, 10000), $v % 100);
```
