# libtreesitter/libtreesitter examples

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
