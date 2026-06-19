# libdbus/libdbus examples

```php
use Pnlx\Libdbus\Libdbus;

// dbus_get_version writes major/minor/micro through int* out-parameters (no bus needed).
$major = 0; $minor = 0; $micro = 0;
Libdbus::dbus_get_version($major, $minor, $micro);
echo "libdbus {$major}.{$minor}.{$micro}\n";
```
