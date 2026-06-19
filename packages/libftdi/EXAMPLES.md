# libftdi/libftdi examples

```php
use Pnlx\Libftdi\Libftdi;

// ftdi_new() allocates and initialises a context (no device needed); free it again.
$ctx = Libftdi::ftdi_new();
echo $ctx !== null ? "ftdi context created\n" : "ftdi_new() failed\n";
if ($ctx !== null) {
    Libftdi::ftdi_free($ctx);
}
```
