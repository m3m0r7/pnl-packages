# ncurses Package

Package: `libncurses/libncurses`

Base library: ncurses

License: X11

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libncurses
```

The package requires ncurses headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libncurses` finishes — it comes from the package's `examples` field in `pnlx.json`.
