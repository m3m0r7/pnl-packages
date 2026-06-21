# GDBM Package

Package: `libgdbm/libgdbm`

License: GPL-3.0-or-later

## PHP usage

```php
use Pnlx\Libgdbm\Libgdbm;

// gdbm_open() creates/opens a database (mode 3 = GDBM_NEWDB, always a fresh db);
// the trailing fatal-error callback is optional, so pass null. gdbm_close() frees it.
$path = sys_get_temp_dir() . '/pnlx_gdbm_demo.db';
$db = Libgdbm::gdbm_open($path, 512, 3, 0644, null);
echo ($db === null ? 'gdbm_open failed' : 'gdbm opened') . PHP_EOL;
Libgdbm::gdbm_close($db);
```
