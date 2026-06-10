# liblzma/liblzma examples

```php
use Pnlx\Liblzma\Liblzma;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$liblzma = $runtime->load(Liblzma::class);

// Query the liblzma runtime version string and number.
$verStr = $liblzma->lzma_version_string(); // returns string, e.g. "5.6.1"
$verNum = $liblzma->lzma_version_number(); // returns int, e.g. 50060010
echo 'liblzma version: ' . $verStr . ' (' . $verNum . ')' . PHP_EOL;
// Main entry points to explore: lzma_easy_encoder, lzma_stream_decoder,
// lzma_code, lzma_end for streaming XZ/LZMA2 compression.
```
