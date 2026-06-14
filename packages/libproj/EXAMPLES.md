# libproj/libproj examples

```php
use Pnlx\Libproj\Libproj;

// proj_context_create() makes a threading context; free it when done.
$ctx = Libproj::proj_context_create();
Libproj::proj_context_destroy($ctx);

// Explore further: proj_create_crs_to_crs(), proj_trans(),
// proj_normalize_for_visualization(), proj_destroy(), ...
```
