# libncurses/libncurses examples

```php
use Pnlx\Libncurses\Libncurses;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libncurses = $runtime->load(Libncurses::class);

// Initialise the terminal, print a message, wait for a key, then exit
$libncurses->initscr();
$libncurses->cbreak();
$libncurses->noecho();

$libncurses->mvprintw(0, 0, "Hello from ncurses!");
$libncurses->refresh();
$libncurses->getch();

$libncurses->endwin();
```
