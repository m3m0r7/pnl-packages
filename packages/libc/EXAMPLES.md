# libc/libc examples

```php
use Pnlx\Libc\Libc;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libc = $runtime->load(Libc::class);

$libc->printf("Hello, World from libc!\n");
$libc->puts("And this line is printed by libc puts.");
```
