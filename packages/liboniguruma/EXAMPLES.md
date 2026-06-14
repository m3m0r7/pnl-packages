# liboniguruma/liboniguruma examples

```php
use Pnlx\Liboniguruma\Liboniguruma;
use function Pnlx\Util\is_null;

$liboniguruma = new Liboniguruma();

// Query library version (char* → PHP string)
$version = $liboniguruma->onig_version();
echo "Oniguruma version: $version\n";

// Compile a regex and search a string
$regex = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$err   = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$pattern = 'hel+o';
$liboniguruma->onig_new($regex, $pattern, $pattern, 0, 0, null, $err);
// ... use onig_search() / onig_free() ...
// $liboniguruma->onig_free($regex);
```
