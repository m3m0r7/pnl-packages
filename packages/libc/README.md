# libc

A zero-dependency pnl package that wraps a few functions from the C standard
library (`printf`, `puts`).

libc is part of the operating system — it ships with macOS (as part of
libSystem, in the dyld shared cache), Linux (glibc/musl), and Windows — so there
is nothing to install. The library entries are marked `"virtual": true`, which
tells pnl to link them by name without requiring a file on disk.

```sh
pnl install libc
```

```php
$libc = $runtime->load(Pnlx\Libc\Libc::class);
$libc->printf("Hello, World from libc!\n");
```
