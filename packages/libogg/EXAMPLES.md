# libogg/libogg examples

```php
use Pnlx\Libogg\Libogg;

// Initialise a sync state for reading an Ogg bitstream from a file
$syncState = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
Libogg::ogg_sync_init($syncState);

// Write raw bytes into the sync buffer
$buf = Libogg::ogg_sync_buffer($syncState, 4096);
$bytes = fread(fopen('file.ogg', 'rb'), 4096);
// ... copy $bytes into $buf, then call ogg_sync_wrote() ...
Libogg::ogg_sync_wrote($syncState, strlen($bytes));

// Parse pages and submit to a stream state
$streamState = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
Libogg::ogg_stream_init($streamState, 1);
// ... ogg_sync_pageout() / ogg_stream_packetout() loop ...
Libogg::ogg_stream_clear($streamState);
Libogg::ogg_sync_clear($syncState);
```
