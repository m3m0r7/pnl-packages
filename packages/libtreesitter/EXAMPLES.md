# libtreesitter/libtreesitter examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtreesitter\Libtreesitter;
use function Pnlx\Util\is_null;

// Create a parser (language must be set before parsing).
$parser = Libtreesitter::ts_parser_new();
if (is_null($parser)) { throw new \RuntimeException('ts_parser_new failed'); }

// Set the language, then parse source code into a syntax tree.
// Libtreesitter::ts_parser_set_language($parser, $lang);
// $tree = Libtreesitter::ts_parser_parse_string($parser, null, $src, strlen($src));
// $root = Libtreesitter::ts_tree_root_node($tree);
Libtreesitter::ts_parser_delete($parser);
```
