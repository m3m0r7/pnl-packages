# libtreesitter/libtreesitter query cursor match limit

Create a query cursor and inspect or tune its match limit without needing a language, query, or syntax tree.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtreesitter\Libtreesitter;
use function Pnlx\Util\is_null;

// A query cursor tracks query execution; its match limit can be tuned without
// any language, query, or syntax tree.
$cursor = Libtreesitter::ts_query_cursor_new();
if (is_null($cursor)) { throw new \RuntimeException('ts_query_cursor_new failed'); }

$default = Libtreesitter::ts_query_cursor_match_limit($cursor);
echo 'default match limit: ' . (is_object($default) ? $default->toInt() : $default) . "\n"; // 4294967295

Libtreesitter::ts_query_cursor_set_match_limit($cursor, 32);
$updated = Libtreesitter::ts_query_cursor_match_limit($cursor);
echo 'updated match limit: ' . (is_object($updated) ? $updated->toInt() : $updated) . "\n"; // 32

$exceeded = Libtreesitter::ts_query_cursor_did_exceed_match_limit($cursor);
echo 'exceeded limit: ' . ((is_object($exceeded) ? $exceeded->toInt() : $exceeded) ? 'yes' : 'no') . "\n"; // no

Libtreesitter::ts_query_cursor_delete($cursor);
```
