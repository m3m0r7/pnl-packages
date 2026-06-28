# libjasper memory configuration

Reset the JasPer library configuration, query the total system memory it can see, and cap its memory budget at half of that.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libjasper\Libjasper;

// Reset config, read the detected system memory, then set a memory limit.
Libjasper::jas_conf_clear();

$total = Libjasper::jas_get_total_mem_size();
$total = is_object($total) ? $total->toInt() : $total;
echo 'total system memory JasPer sees: ' . $total . ' bytes' . PHP_EOL;

$limit = intdiv($total, 2);
Libjasper::jas_conf_set_max_mem_usage($limit);
echo 'configured JasPer memory limit: ' . $limit . ' bytes' . PHP_EOL;
```
