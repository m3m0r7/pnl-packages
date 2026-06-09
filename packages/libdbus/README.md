# D-Bus Package

Package: `libdbus/libdbus`

Base library: D-Bus

License: AFL-2.1

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libdbus
```

The package requires D-Bus headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libdbus\Libdbus;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libdbus = $runtime->load(Libdbus::class);

// dbus_get_local_machine_id() returns the machine's D-Bus UUID as a string.
$machineId = $libdbus->dbus_get_local_machine_id();
echo "Machine ID: " . $machineId . PHP_EOL;

// Retrieve library version components via out-parameters.
$allocator = $runtime->allocator();
$major = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$minor = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$micro = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$libdbus->dbus_get_version($major, $minor, $micro);
echo "libdbus version: {$major->cdata}.{$minor->cdata}.{$micro->cdata}" . PHP_EOL;
```

This snippet is printed when `pnl install libdbus` finishes — it comes from the package's `examples` field in `pnlx.json`.
