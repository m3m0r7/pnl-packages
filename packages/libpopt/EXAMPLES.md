# libpopt/libpopt examples

```php
use Pnlx\Libpopt\Libpopt;

// poptStrerror() turns a popt error code into a readable message.
$message = Libpopt::poptStrerror(-10);
echo "popt: $message\n";

// Explore further: poptGetContext(), poptGetNextOpt(),
// poptGetArg(), poptFreeContext(), ...
```
