# libreadline/libreadline variables & history state

`rl_variable_value()` reads a Readline configuration variable, and `using_history()` / `where_history()` / `history_is_stifled()` query the history state — all without opening a terminal.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libreadline\Libreadline;

// rl_variable_value() returns the current value of a Readline variable.
echo 'editing-mode: ' . (string) Libreadline::rl_variable_value('editing-mode') . "\n"; // emacs

// using_history() initialises the history session.
Libreadline::using_history();

// where_history() is the current position in the (empty) history list.
$where = Libreadline::where_history();
echo 'where_history: ' . (is_object($where) ? $where->toInt() : $where) . "\n"; // 0

// history_is_stifled() reports whether the history size is capped.
$stifled = Libreadline::history_is_stifled();
echo 'history_is_stifled: ' . (is_object($stifled) ? $stifled->toInt() : $stifled) . "\n"; // 0
```
