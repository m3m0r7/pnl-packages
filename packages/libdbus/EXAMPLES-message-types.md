# libdbus/libdbus message-type helpers

These pure helpers need no bus connection: `dbus_message_type_to_string()` and `dbus_message_type_from_string()` translate D-Bus message-type codes to names and back, and `dbus_address_escape_value()` escapes a value for use in a D-Bus address string.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libdbus\Libdbus;

// Pure helpers that need no bus connection: translate message-type codes to
// names and back, and escape a value for use in a D-Bus address.
$num = static fn($x) => is_object($x) ? $x->toInt() : $x;

// DBUS_MESSAGE_TYPE_*: 1=method_call, 2=method_return, 3=error, 4=signal.
foreach ([1, 2, 3, 4] as $type) {
    echo "type {$type} => " . (string) Libdbus::dbus_message_type_to_string($type) . PHP_EOL;
}

echo "'signal' => " . $num(Libdbus::dbus_message_type_from_string('signal')) . PHP_EOL;
echo 'escaped: ' . (string) Libdbus::dbus_address_escape_value('hello world/42') . PHP_EOL;
```
