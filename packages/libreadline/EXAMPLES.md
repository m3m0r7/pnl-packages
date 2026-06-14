# libreadline/libreadline examples

```php
use Pnlx\Libreadline\Libreadline;

// Initialise the Readline library explicitly
Libreadline::rl_initialize();

// Read a line from stdin with an interactive prompt.
// readline() returns a PHP string (malloc-allocated in C); add it to history
// so the user can recall it with the up-arrow key, then free the C buffer.
$line = Libreadline::readline('Enter command: ');
if ($line !== null) {
    echo "You entered: {$line}\n";
    Libreadline::add_history($line);
    Libreadline::rl_free($line);
}
// For batch history save/restore: Libreadline::write_history('~/.myapp_history')
//                               / Libreadline::read_history('~/.myapp_history')
```
