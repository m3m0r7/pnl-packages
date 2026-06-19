# libreadline/libreadline examples

```php
use Pnlx\Libreadline\Libreadline;

// tilde_expand() expands a leading ~ to the home directory — a pure call that needs
// no terminal.
echo Libreadline::tilde_expand('~/.bashrc') . "\n"; // e.g. /root/.bashrc
```
