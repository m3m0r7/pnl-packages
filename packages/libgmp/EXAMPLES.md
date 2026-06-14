# libgmp/libgmp examples

```php
use Pnlx\Libgmp\Libgmp;

// Arbitrary-precision addition: a + b -> result printed as decimal string
$a = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$b = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$result = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);

Libgmp::__gmpz_init($a);
Libgmp::__gmpz_init($b);
Libgmp::__gmpz_init($result);
Libgmp::__gmpz_set_str($a, '123456789012345678901234567890', 10);
Libgmp::__gmpz_set_str($b, '987654321098765432109876543210', 10);
Libgmp::__gmpz_add($result, $a, $b);
echo Libgmp::__gmpz_get_str(null, 10, $result) . "\n";
Libgmp::__gmpz_clear($a);
Libgmp::__gmpz_clear($b);
Libgmp::__gmpz_clear($result);
```
