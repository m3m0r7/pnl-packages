# libtcc/libtcc examples

```php
use Pnlx\Libtcc\Libtcc;
use function Pnlx\Util\is_null;

// Create a TinyCC compilation context.
$tcc = Libtcc::tcc_new();
if (is_null($tcc)) { throw new \RuntimeException('tcc_new failed'); }

// Compile a C string in memory and run it.
Libtcc::tcc_set_output_type($tcc, 1 /* TCC_OUTPUT_MEMORY */);
Libtcc::tcc_compile_string($tcc, 'int add(int a,int b){return a+b;}');
Libtcc::tcc_relocate($tcc);
// $fn = Libtcc::tcc_get_symbol($tcc, 'add'); // returns FFI\CData pointer
Libtcc::tcc_delete($tcc);
```
