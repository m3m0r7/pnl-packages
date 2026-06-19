# libbz2/libbz2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libbz2\Libbz2;
use function Pnlx\Util\is_null;

// Open a file for bzip2-compressed writing, write data, then close it
$bzfile = Libbz2::BZ2_bzopen('output.bz2', 'w');
if (is_null($bzfile)) {
    throw new \RuntimeException('BZ2_bzopen failed');
}
$data = 'Hello, bzip2 compression!';
Libbz2::BZ2_bzwrite($bzfile, $data, strlen($data));
Libbz2::BZ2_bzclose($bzfile);
echo "bzip2: compressed " . strlen($data) . " bytes to output.bz2\n";

// Open for reading: Libbz2::BZ2_bzopen('output.bz2', 'r')
// then: Libbz2::BZ2_bzread($bzfile, $buf, $len)
```
