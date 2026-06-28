# libgumbo/libgumbo tag names

`gumbo_tag_enum()` maps an HTML tag name to its `GumboTag` enum value, and `gumbo_normalized_tagname()` maps that enum back to the canonical name.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgumbo\Libgumbo;

// gumbo_tag_enum() maps an HTML tag name to its GumboTag enum value, and
// gumbo_normalized_tagname() maps that enum back to the canonical name.
foreach (['div', 'h1', 'svg'] as $name) {
    $tag = Libgumbo::gumbo_tag_enum($name);
    $tag = is_object($tag) ? $tag->toInt() : $tag;
    $back = (string) Libgumbo::gumbo_normalized_tagname($tag);
    echo "{$name} -> enum {$tag} -> {$back}\n";
}
```
