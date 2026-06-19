# libc/libc examples

```php
use Pnlx\Libc\Libc;

// With the scalar-friendly feature flags, plain PHP scalars go straight in and out.
Libc::puts('Hello, World from libc!');                  // prints the line, returns >= 0
printf("strcmp: %d\n", Libc::strcmp('abc', 'abd'));     // negative
printf("toupper: %s\n", chr(Libc::toupper(ord('p'))));  // P
printf("strstr: %s\n", Libc::strstr('native php', 'php')); // php
```
