# libflac/libflac examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libflac\Libflac;
use function Pnlx\Util\is_null;

// Create a stream decoder.
$decoder = Libflac::FLAC__stream_decoder_new();
if (is_null($decoder)) {
    throw new \RuntimeException('FLAC__stream_decoder_new() failed');
}

// Enable MD5 verification during decoding.
Libflac::FLAC__stream_decoder_set_md5_checking($decoder, 1);

// FLAC__stream_decoder_init_file(decoder, path, write_cb, metadata_cb, error_cb, client)
// attaches the decoder to a .flac file; use FLAC__stream_decoder_process_until_end_of_stream()
// to fully decode it.

Libflac::FLAC__stream_decoder_delete($decoder);
echo "Decoder created and released." . PHP_EOL;
```
