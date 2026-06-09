# Oniguruma Package

Package: `liboniguruma/liboniguruma`

Base library: Oniguruma

License: BSD-2-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liboniguruma
```

The package requires Oniguruma headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install liboniguruma` finishes — it comes from the package's `examples` field in `pnlx.json`.
