# libgraphite2/libgraphite2 tag packing

`gr_str_to_tag()` packs a 4-character OpenType-style identifier into the 32-bit unsigned tag integer Graphite uses for languages and features.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgraphite2\Libgraphite2;

// gr_str_to_tag() packs a 4-character OpenType-style identifier into the
// 32-bit unsigned tag integer Graphite uses for languages and features.
foreach (['Latn', 'kern', 'smcp'] as $name) {
    $tag = Libgraphite2::gr_str_to_tag($name);
    $tag = is_object($tag) ? $tag->toInt() : $tag;
    echo sprintf("%s -> 0x%08X\n", $name, $tag);
}
```
