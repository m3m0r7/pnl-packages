# libgmp/libgmp examples

```php
use Pnlx\Libgmp\Libgmp;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libgmp = $runtime->load(Libgmp::class);

// Arbitrary-precision addition: a + b -> result printed as decimal string
$a = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$b = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$result = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);

$libgmp->__gmpz_init($a);
$libgmp->__gmpz_init($b);
$libgmp->__gmpz_init($result);
$libgmp->__gmpz_set_str($a, '123456789012345678901234567890', 10);
$libgmp->__gmpz_set_str($b, '987654321098765432109876543210', 10);
$libgmp->__gmpz_add($result, $a, $b);
echo $libgmp->__gmpz_get_str(null, 10, $result) . "\n";
$libgmp->__gmpz_clear($a);
$libgmp->__gmpz_clear($b);
$libgmp->__gmpz_clear($result);
```
