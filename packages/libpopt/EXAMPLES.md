# libpopt/libpopt examples

```php
use Pnlx\Libpopt\Libpopt;

$libpopt = new Libpopt();

// poptStrerror() turns a popt error code into a readable message.
$message = $libpopt->poptStrerror(-10);
echo "popt: $message\n";

// Explore further: poptGetContext(), poptGetNextOpt(),
// poptGetArg(), poptFreeContext(), ...
```
