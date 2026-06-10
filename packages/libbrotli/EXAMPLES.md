# libbrotli/libbrotli examples

```php
use Pnlx\Libbrotli\Libbrotli;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libbrotli = $runtime->load(Libbrotli::class);

// Print the Brotli encoder version number
$version = $libbrotli->BrotliEncoderVersion();
$major   = ($version >> 24) & 0xff;
$minor   = ($version >> 12) & 0xfff;
$patch   = $version & 0xfff;
echo "Brotli encoder version: {$major}.{$minor}.{$patch}\n";

// Compute the maximum compressed size for a given input length
$inputLen    = 1024;
$maxEncoded  = $libbrotli->BrotliEncoderMaxCompressedSize($inputLen);
echo "Max compressed size for {$inputLen} bytes: {$maxEncoded}\n";

// Compress/decompress: $libbrotli->BrotliEncoderCompress(quality, window, mode, inputLen, input, $encodedSize, $encodedBuf)
// then: $libbrotli->BrotliDecoderDecompress($encodedSize, $encodedBuf, $decodedSize, $decodedBuf)
```
