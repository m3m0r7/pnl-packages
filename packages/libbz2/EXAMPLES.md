# libbz2/libbz2 examples

```php
use Pnlx\Libbz2\Libbz2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libbz2 = $runtime->load(Libbz2::class);

// Open a file for bzip2-compressed writing, write data, then close it
$bzfile = $libbz2->BZ2_bzopen('output.bz2', 'w');
if (\is_null($bzfile)) {
    throw new \RuntimeException('BZ2_bzopen failed');
}
$data = 'Hello, bzip2 compression!';
$libbz2->BZ2_bzwrite($bzfile, $data, strlen($data));
$libbz2->BZ2_bzclose($bzfile);

// Open for reading: $libbz2->BZ2_bzopen('output.bz2', 'r')
// then: $libbz2->BZ2_bzread($bzfile, $buf, $len)
```
