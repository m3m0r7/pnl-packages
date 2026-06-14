# libbrotli/libbrotli examples

```php
use Pnlx\Libbrotli\Libbrotli;

// Print the Brotli encoder version number
$version = Libbrotli::BrotliEncoderVersion();
$major   = ($version >> 24) & 0xff;
$minor   = ($version >> 12) & 0xfff;
$patch   = $version & 0xfff;
echo "Brotli encoder version: {$major}.{$minor}.{$patch}\n";

// Compute the maximum compressed size for a given input length
$inputLen    = 1024;
$maxEncoded  = Libbrotli::BrotliEncoderMaxCompressedSize($inputLen);
echo "Max compressed size for {$inputLen} bytes: {$maxEncoded}\n";

// Compress/decompress: Libbrotli::BrotliEncoderCompress(quality, window, mode, inputLen, input, $encodedSize, $encodedBuf)
// then: Libbrotli::BrotliDecoderDecompress($encodedSize, $encodedBuf, $decodedSize, $decodedBuf)
```
