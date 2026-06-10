# libflac/libflac examples

```php
use Pnlx\Libflac\Libflac;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libflac = $runtime->load(Libflac::class);

// Create a stream decoder.
$decoder = $libflac->FLAC__stream_decoder_new();
if (is_null($decoder)) {
    throw new \RuntimeException('FLAC__stream_decoder_new() failed');
}

// Enable MD5 verification during decoding.
$libflac->FLAC__stream_decoder_set_md5_checking($decoder, 1);

// FLAC__stream_decoder_init_file(decoder, path, write_cb, metadata_cb, error_cb, client)
// attaches the decoder to a .flac file; use FLAC__stream_decoder_process_until_end_of_stream()
// to fully decode it.

$libflac->FLAC__stream_decoder_delete($decoder);
echo "Decoder created and released." . PHP_EOL;
```
