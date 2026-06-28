# libhdf5 library lifecycle

Explicitly initialize the HDF5 library, reclaim its internal free-list memory, then shut it down cleanly.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhdf5\Libhdf5;

$n = fn($x) => is_object($x) ? $x->toInt() : $x;

// Explicitly initialize the HDF5 library (normally done lazily on first use).
$opened = $n(Libhdf5::H5open());
echo "H5open status: {$opened}\n"; // 0 on success

// Ask HDF5 to reclaim the memory held in its internal free lists.
$gc = $n(Libhdf5::H5garbage_collect());
echo "H5garbage_collect status: {$gc}\n"; // 0 on success

// Flush buffers and shut the library down cleanly.
$closed = $n(Libhdf5::H5close());
echo "H5close status: {$closed}\n"; // 0 on success
```
