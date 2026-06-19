# libgmp/libgmp examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgmp\Libgmp;
use Pnlx\Libgmp\Types\__mpz_struct;

// mpz_ptr is __mpz_struct*; allocate the structs with `new __mpz_struct()`.
$a = new __mpz_struct();
$b = new __mpz_struct();
$result = new __mpz_struct();

Libgmp::__gmpz_init($a);
Libgmp::__gmpz_init($b);
Libgmp::__gmpz_init($result);

Libgmp::__gmpz_set_str($a, '123456789012345678901234567890', 10);
Libgmp::__gmpz_set_str($b, '987654321098765432109876543210', 10);
Libgmp::__gmpz_add($result, $a, $b);

// __gmpz_get_str writes the decimal string into a char* buffer (by reference).
$buf = str_repeat("\0", 64);
Libgmp::__gmpz_get_str($buf, 10, $result);
echo rtrim($buf, "\0") . "\n"; // 1111111110111111111011111111100

Libgmp::__gmpz_clear($a);
Libgmp::__gmpz_clear($b);
Libgmp::__gmpz_clear($result);
```
