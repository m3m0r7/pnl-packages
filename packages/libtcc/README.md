# TinyCC Package

Package: `libtcc/libtcc`

Base library: TinyCC

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libtcc
```

The package requires TinyCC headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libtcc\Libtcc;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libtcc = $runtime->load(Libtcc::class);

// Create a TinyCC compilation context.
$tcc = $libtcc->tcc_new();
if (is_null($tcc)) { throw new \RuntimeException('tcc_new failed'); }

// Compile a C string in memory and run it.
$libtcc->tcc_set_output_type($tcc, 1 /* TCC_OUTPUT_MEMORY */);
$libtcc->tcc_compile_string($tcc, 'int add(int a,int b){return a+b;}');
$libtcc->tcc_relocate($tcc);
// $fn = $libtcc->tcc_get_symbol($tcc, 'add'); // returns FFI\CData pointer
$libtcc->tcc_delete($tcc);
```

This snippet is printed when `pnl install libtcc` finishes — it comes from the package's `examples` field in `pnlx.json`.
