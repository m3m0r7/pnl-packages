# zlib/zlib examples

```php
use Pnlx\Zlib\Zlib;

// zlibVersion() returns the library version string, e.g. "1.3.1".
$version = Zlib::zlibVersion();
echo "zlib version: $version\n";

// compressBound(sourceLen) returns the worst-case compressed size.
$bound = Zlib::compressBound(1024);
echo "Max compressed size for 1024 bytes: $bound\n";

// Explore further: compress2(), uncompress(), deflateInit(),
// deflate(), deflateEnd(), inflateInit(), inflate(), inflateEnd(), ...
```
