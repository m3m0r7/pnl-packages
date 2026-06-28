# libopenjp2/libopenjp2 threading capabilities

Query OpenJPEG's multithreading support and the number of CPUs it can use without touching any codec.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libopenjp2\Libopenjp2;

// opj_has_thread_support() reports whether the build supports multithreading.
$threads = Libopenjp2::opj_has_thread_support();
$threads = is_object($threads) ? $threads->toInt() : $threads;
echo 'Thread support: ' . ($threads ? 'yes' : 'no') . "\n";

// opj_get_num_cpus() returns the number of CPUs OpenJPEG can use.
$cpus = Libopenjp2::opj_get_num_cpus();
$cpus = is_object($cpus) ? $cpus->toInt() : $cpus;
echo "Available CPUs: $cpus\n";
```
