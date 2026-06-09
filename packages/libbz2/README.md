# bzip2 Package

Package: `libbz2/libbz2`

Base library: bzip2

License: bzip2-1.0.6

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libbz2
```

The package requires bzip2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libbz2` finishes — it comes from the package's `examples` field in `pnlx.json`.
