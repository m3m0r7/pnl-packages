# libevent/libevent introspection examples

Query libevent's packed version number and internal `struct event` size, and translate a getaddrinfo() error code into a message.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libevent\Libevent;

// Packed numeric version of libevent, e.g. 0x02010c00 for 2.1.12.
$num = Libevent::event_get_version_number();
$num = is_object($num) ? $num->toInt() : $num;
printf("version number: 0x%08x" . PHP_EOL, $num);

// Size, in bytes, of libevent's internal `struct event`.
$size = Libevent::event_get_struct_event_size();
$size = is_object($size) ? $size->toInt() : $size;
echo "struct event size: " . $size . " bytes" . PHP_EOL;

// Translate a getaddrinfo() error code into a human-readable string.
$msg = Libevent::evutil_gai_strerror(0);
echo "gai_strerror(0): " . (string)$msg . PHP_EOL;
```
