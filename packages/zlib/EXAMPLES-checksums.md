# zlib/zlib checksum examples

A second example exercising a different part of the API: the running checksums
(`crc32`, `adler32`) and the build configuration (`zlibCompileFlags`).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Zlib\Zlib;

$data = 'hello world';

// crc32(crc, buf, len): seed with 0, then fold in the bytes. `const Bytef *`
// accepts a PHP string directly.
$crc = Zlib::crc32(0, $data, strlen($data));
echo 'crc32: ' . $crc->toInt() . "\n";

// adler32(adler, buf, len): the Adler-32 checksum is seeded with 1.
$adler = Zlib::adler32(1, $data, strlen($data));
echo 'adler32: ' . $adler->toInt() . "\n";

// zlibCompileFlags() reports the type sizes and options zlib was built with.
$flags = Zlib::zlibCompileFlags();
echo 'compile flags: ' . $flags->toInt() . "\n";
```
