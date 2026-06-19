# libfreetype/libfreetype examples

```php
use Pnlx\Libfreetype\Libfreetype;

// FT_Init_FreeType writes a new FT_Library handle through its out-parameter
// (FT_Library* → by reference). $library comes back holding the handle.
$library = null;
if (Libfreetype::FT_Init_FreeType($library) !== 0) {
    throw new \RuntimeException('FT_Init_FreeType failed');
}

// FT_Library_Version takes the handle and writes the version through int* out-params.
$major = 0; $minor = 0; $patch = 0;
Libfreetype::FT_Library_Version($library, $major, $minor, $patch);
echo "FreeType {$major}.{$minor}.{$patch}\n";

Libfreetype::FT_Done_FreeType($library);
```
