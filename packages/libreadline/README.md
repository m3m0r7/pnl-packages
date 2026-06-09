# GNU Readline Package

Package: `libreadline/libreadline`

Base library: GNU Readline

License: GPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libreadline
```

The package requires GNU Readline headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libreadline\Libreadline;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libreadline = $runtime->load(Libreadline::class);

// Initialise the Readline library explicitly
$libreadline->rl_initialize();

// Read a line from stdin with an interactive prompt.
// readline() returns a PHP string (malloc-allocated in C); add it to history
// so the user can recall it with the up-arrow key, then free the C buffer.
$line = $libreadline->readline('Enter command: ');
if ($line !== null) {
    echo "You entered: {$line}\n";
    $libreadline->add_history($line);
    $libreadline->rl_free($line);
}
// For batch history save/restore: $libreadline->write_history('~/.myapp_history')
//                               / $libreadline->read_history('~/.myapp_history')
```

This snippet is printed when `pnl install libreadline` finishes — it comes from the package's `examples` field in `pnlx.json`.
