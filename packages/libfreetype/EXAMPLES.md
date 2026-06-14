# libfreetype/libfreetype examples

```php
use Pnlx\Libfreetype\Libfreetype;

// Initialise the FreeType library and query its version.
$allocator = (new \Pnlx\FFI\Allocator());
$library = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
Libfreetype::FT_Init_FreeType($library);

$major = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$minor = $allocator->make(\Pnlx\FFI\AllocationType::Int);
$patch = $allocator->make(\Pnlx\FFI\AllocationType::Int);
Libfreetype::FT_Library_Version($library->cdata, $major, $minor, $patch);
echo "FreeType version: {$major->cdata}.{$minor->cdata}.{$patch->cdata}" . PHP_EOL;

// FT_New_Face() loads a font file; FT_Done_FreeType() tears down.
Libfreetype::FT_Done_FreeType($library->cdata);
```
