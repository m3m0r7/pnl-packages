# libnlopt/libnlopt algorithm and result introspection

Look up the descriptive name of an optimization algorithm, turn a result code into its symbolic name, and read the default stochastic population size.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnlopt\Libnlopt;

// nlopt_algorithm_name() returns the descriptive name of an algorithm enum value.
$name = Libnlopt::nlopt_algorithm_name(24); // NLOPT_LD_MMA
echo 'algorithm_name(24): ' . (string)$name . "\n"; // Method of Moving Asymptotes (MMA) (local, derivative)

// nlopt_result_to_string() turns a result code into its symbolic name.
$result = Libnlopt::nlopt_result_to_string(1); // NLOPT_SUCCESS
echo 'result_to_string(1): ' . (string)$result . "\n"; // SUCCESS

// nlopt_get_stochastic_population() reports the default stochastic population size.
$pop = Libnlopt::nlopt_get_stochastic_population();
echo 'stochastic_population: ' . (is_object($pop) ? $pop->toInt() : $pop) . "\n"; // 0
```
