# libpq/libpq examples

```php
use Pnlx\Libpq\Libpq;

// PQlibVersion() reports the client library version without connecting to a server.
$v = Libpq::PQlibVersion();
printf("libpq %d.%d\n", intdiv($v, 10000), $v % 100);
```
