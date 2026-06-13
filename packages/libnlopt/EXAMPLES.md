# libnlopt/libnlopt examples

```php
use Pnlx\Libnlopt\Libnlopt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnlopt = $runtime->load(Libnlopt::class);

// Create an optimizer over 2 variables (NLOPT_LD_MMA = 24), then free it.
$opt = $libnlopt->nlopt_create(24, 2);
$libnlopt->nlopt_destroy($opt);

// Explore further: nlopt_set_min_objective(), nlopt_set_xtol_rel(),
// nlopt_optimize(), nlopt_set_lower_bounds(), ...
```
