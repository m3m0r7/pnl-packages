# libbrotli/libbrotli examples

`libbrotli` binds the Brotli **encoder** and **decoder** — which live in two
separate shared libraries (`libbrotlienc` and `libbrotlidec`) — through a single
entity. The decoder is the package's own library and the encoder is co-loaded via
`dependencies`, so both APIs are callable from `Pnlx\Libbrotli\Libbrotli`.

```php
use Pnlx\Libbrotli\Libbrotli;

// Versions (encoder lives in libbrotlienc, decoder in libbrotlidec).
$v = (int) (string) Libbrotli::BrotliEncoderVersion();
printf("Brotli %d.%d.%d\n", ($v >> 24) & 0xff, ($v >> 12) & 0xfff, $v & 0xfff);

// Round-trip: compress with the encoder, decompress with the decoder.
$input    = "Hello, Brotli! " . str_repeat("compress me ", 30);
$inputLen = strlen($input);

// Encode.
$capacity    = (int) (string) Libbrotli::BrotliEncoderMaxCompressedSize($inputLen);
$encodedSize = $capacity;                 // in: buffer capacity, out: encoded length
$encodedBuf  = str_repeat("\0", $capacity);
Libbrotli::BrotliEncoderCompress(11, 22, 0, $inputLen, $input, $encodedSize, $encodedBuf);
$compressed  = substr($encodedBuf, 0, (int) (string) $encodedSize);
printf("compressed %d -> %d bytes\n", $inputLen, strlen($compressed));

// Decode.
$decodedSize = $inputLen;                 // in: buffer capacity, out: decoded length
$decodedBuf  = str_repeat("\0", $inputLen);
Libbrotli::BrotliDecoderDecompress(strlen($compressed), $compressed, $decodedSize, $decodedBuf);
$decoded     = substr($decodedBuf, 0, (int) (string) $decodedSize);

echo $decoded === $input ? "round-trip OK\n" : "mismatch\n";
```
