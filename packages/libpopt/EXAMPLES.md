# libpopt/libpopt examples

```php
use Pnlx\Libpopt\Libpopt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libpopt = $runtime->load(Libpopt::class);

// poptStrerror() turns a popt error code into a readable message.
$message = $libpopt->poptStrerror(-10);
echo "popt: $message\n";

// Explore further: poptGetContext(), poptGetNextOpt(),
// poptGetArg(), poptFreeContext(), ...
```
