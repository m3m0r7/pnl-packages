# libtcc/libtcc examples

```php
use Pnlx\Libtcc\Libtcc;
use function Pnlx\Util\is_null;

$libtcc = new Libtcc();

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
