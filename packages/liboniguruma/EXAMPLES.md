# liboniguruma/liboniguruma examples

```php
use Pnlx\Liboniguruma\Liboniguruma;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$liboniguruma = $runtime->load(Liboniguruma::class);

// Query library version (char* → PHP string)
$version = $liboniguruma->onig_version();
echo "Oniguruma version: $version\n";

// Compile a regex and search a string
$regex = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$err   = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$pattern = 'hel+o';
$liboniguruma->onig_new($regex, $pattern, $pattern, 0, 0, null, $err);
// ... use onig_search() / onig_free() ...
// $liboniguruma->onig_free($regex);
```
