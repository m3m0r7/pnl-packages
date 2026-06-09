# FreeType Package

Package: `libfreetype/libfreetype`

Base library: FreeType

License: FTL

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libfreetype
```

The package requires FreeType headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libfreetype\Libfreetype;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libfreetype = $runtime->load(Libfreetype::class);

// Initialise the FreeType library and query its version.
$allocator = $runtime->allocator();
$library = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libfreetype->FT_Init_FreeType($library);

$major = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$minor = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$patch = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$libfreetype->FT_Library_Version($library->cdata, $major, $minor, $patch);
echo "FreeType version: {$major->cdata}.{$minor->cdata}.{$patch->cdata}" . PHP_EOL;

// FT_New_Face() loads a font file; FT_Done_FreeType() tears down.
$libfreetype->FT_Done_FreeType($library->cdata);
```

This snippet is printed when `pnl install libfreetype` finishes — it comes from the package's `examples` field in `pnlx.json`.
