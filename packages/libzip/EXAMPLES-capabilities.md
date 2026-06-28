# libzip version and capability probes

Query the linked libzip version and ask whether a given compression or encryption method is supported, without opening an archive.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libzip\Libzip;

// zip_libzip_version() returns the linked libzip version string.
$ver = Libzip::zip_libzip_version();
echo 'libzip version: ' . (string)$ver . PHP_EOL;

// zip_compression_method_supported() reports whether a method can (de)compress.
$deflate = Libzip::zip_compression_method_supported(8, 1); // ZIP_CM_DEFLATE
echo 'deflate supported: ' . (is_object($deflate) ? $deflate->toInt() : $deflate) . PHP_EOL;

// zip_encryption_method_supported() reports whether an encryption method works.
$aes = Libzip::zip_encryption_method_supported(0x0101, 1); // ZIP_EM_AES_128
echo 'AES-128 supported: ' . (is_object($aes) ? $aes->toInt() : $aes) . PHP_EOL;
```
