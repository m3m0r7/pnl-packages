# libc

A zero-dependency pnl package that declares the portable C standard library
surface exposed by libc: ctype, inttypes, locale, setjmp/longjmp, signal, stdio,
stdlib, string/memory, time, wide-character, and wide-ctype functions.

libc is part of the operating system — it ships with macOS (as part of
libSystem, in the dyld shared cache), Linux (glibc/musl), and Windows — so there
is nothing to install. The library entries are marked `"virtual": true`, which
tells pnl to link them by name without requiring a file on disk.

```sh
pnl install libc
```

```php
use Pnlx\Libc\Libc;
use Pnlx\Helpers\String_;

Libc::puts(new String_("Hello, World from libc!"));
echo Libc::strlen(new String_("pnl"))->toInt(), PHP_EOL;
```
