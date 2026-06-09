# Ogg Package

Package: `libogg/libogg`

Base library: Ogg

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libogg
```

The package requires Ogg headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libogg\Libogg;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libogg = $runtime->load(Libogg::class);

// Initialise a sync state for reading an Ogg bitstream from a file
$syncState = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libogg->ogg_sync_init($syncState);

// Write raw bytes into the sync buffer
$buf = $libogg->ogg_sync_buffer($syncState, 4096);
$bytes = fread(fopen('file.ogg', 'rb'), 4096);
// ... copy $bytes into $buf, then call ogg_sync_wrote() ...
$libogg->ogg_sync_wrote($syncState, strlen($bytes));

// Parse pages and submit to a stream state
$streamState = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libogg->ogg_stream_init($streamState, 1);
// ... ogg_sync_pageout() / ogg_stream_packetout() loop ...
$libogg->ogg_stream_clear($streamState);
$libogg->ogg_sync_clear($syncState);
```

This snippet is printed when `pnl install libogg` finishes — it comes from the package's `examples` field in `pnlx.json`.
