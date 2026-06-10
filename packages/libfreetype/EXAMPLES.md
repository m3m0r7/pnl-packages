# libfreetype/libfreetype examples

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
