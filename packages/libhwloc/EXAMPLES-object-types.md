# libhwloc/libhwloc object type helpers

These pure helpers inspect `hwloc_obj_type_t` values without building a topology: `hwloc_obj_type_string()` names a type, `hwloc_obj_type_is_cache()` tests whether it is a cache level, and `hwloc_compare_types()` orders two types by their typical topology depth.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libhwloc\Libhwloc;

// hwloc_obj_type_string() maps a hwloc_obj_type_t value to its canonical name.
$core = Libhwloc::hwloc_obj_type_string(2); // HWLOC_OBJ_CORE
$pu   = Libhwloc::hwloc_obj_type_string(3); // HWLOC_OBJ_PU
echo "type 2 (CORE) => " . (string)$core . "\n";
echo "type 3 (PU)   => " . (string)$pu . "\n";

// hwloc_obj_type_is_cache() reports whether a type is any cache level.
$isCache = Libhwloc::hwloc_obj_type_is_cache(5); // HWLOC_OBJ_L2CACHE
$isCache = is_object($isCache) ? $isCache->toInt() : $isCache;
echo "L2CACHE is cache? " . ($isCache ? 'yes' : 'no') . "\n";

// hwloc_compare_types() orders two types by their typical topology depth.
$cmp = Libhwloc::hwloc_compare_types(2, 3); // CORE vs PU
$cmp = is_object($cmp) ? $cmp->toInt() : $cmp;
echo "compare(CORE, PU) => " . $cmp . "\n";
```
