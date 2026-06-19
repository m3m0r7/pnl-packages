# libnlopt/libnlopt examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnlopt\Libnlopt;

// Create an optimizer over 2 variables (NLOPT_LD_MMA = 24), then free it.
$opt = Libnlopt::nlopt_create(24, 2);
Libnlopt::nlopt_destroy($opt);

// Explore further: nlopt_set_min_objective(), nlopt_set_xtol_rel(),
// nlopt_optimize(), nlopt_set_lower_bounds(), ...
```
