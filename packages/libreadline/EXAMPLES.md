# libreadline/libreadline examples

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
