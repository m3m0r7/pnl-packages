# libc/libc examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libc\Libc;

// Scalar results come back as \Pnlx\Types\Int_ wrappers; unwrap with ->toInt()
// where a native PHP int is required (printf %d, chr()). String results are
// Stringable, so they drop straight into %s.
Libc::puts('Hello, World from libc!');                          // prints the line, returns >= 0
printf("strcmp: %d\n", Libc::strcmp('abc', 'abd')->toInt());    // negative
printf("toupper: %s\n", chr(Libc::toupper(ord('p'))->toInt())); // P
printf("strstr: %s\n", Libc::strstr('native php', 'php'));      // php
```
