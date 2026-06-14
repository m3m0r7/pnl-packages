# libncurses/libncurses examples

```php
use Pnlx\Libncurses\Libncurses;

// Initialise the terminal, print a message, wait for a key, then exit
Libncurses::initscr();
Libncurses::cbreak();
Libncurses::noecho();

Libncurses::mvprintw(0, 0, "Hello from ncurses!");
Libncurses::refresh();
Libncurses::getch();

Libncurses::endwin();
```
