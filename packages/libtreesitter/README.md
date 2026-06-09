# Tree-sitter Package

Package: `libtreesitter/libtreesitter`

Base library: Tree-sitter

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libtreesitter
```

The package requires Tree-sitter headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libtreesitter\Libtreesitter;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libtreesitter = $runtime->load(Libtreesitter::class);

// Create a parser (language must be set before parsing).
$parser = $libtreesitter->ts_parser_new();
if (is_null($parser)) { throw new \RuntimeException('ts_parser_new failed'); }

// Set the language, then parse source code into a syntax tree.
// $libtreesitter->ts_parser_set_language($parser, $lang);
// $tree = $libtreesitter->ts_parser_parse_string($parser, null, $src, strlen($src));
// $root = $libtreesitter->ts_tree_root_node($tree);
$libtreesitter->ts_parser_delete($parser);
```

This snippet is printed when `pnl install libtreesitter` finishes — it comes from the package's `examples` field in `pnlx.json`.
