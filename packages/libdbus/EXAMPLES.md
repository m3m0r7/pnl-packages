# libdbus/libdbus examples

```php
use Pnlx\Libdbus\Libdbus;

$libdbus = new Libdbus();

// dbus_get_local_machine_id() returns the machine's D-Bus UUID as a string.
$machineId = $libdbus->dbus_get_local_machine_id();
echo "Machine ID: " . $machineId . PHP_EOL;

// Retrieve library version components via out-parameters.
$allocator = (new \Pnlx\FFI\Allocator());
$major = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$minor = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$micro = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$libdbus->dbus_get_version($major, $minor, $micro);
echo "libdbus version: {$major->cdata}.{$minor->cdata}.{$micro->cdata}" . PHP_EOL;
```
