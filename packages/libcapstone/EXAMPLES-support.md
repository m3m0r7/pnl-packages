# libcapstone/libcapstone — feature support & error strings

Query whether an architecture is supported with `cs_support()` and turn `cs_err` codes into messages with `cs_strerror()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcapstone\Libcapstone;
use const Pnlx\Libcapstone\CS_ARCH_X86;

// cs_support() reports whether this build understands a given architecture
// (or option). Returns a wrapped bool; unwrap it with toInt().
$supportsX86 = Libcapstone::cs_support(CS_ARCH_X86->toInt());
echo 'x86 supported: ' . ($supportsX86->toInt() ? 'yes' : 'no') . PHP_EOL;

// cs_strerror() turns a cs_err code into a human-readable message string.
echo 'CS_ERR_OK   : ' . (string) Libcapstone::cs_strerror(0) . PHP_EOL;
echo 'CS_ERR_ARCH : ' . (string) Libcapstone::cs_strerror(2) . PHP_EOL;
```
