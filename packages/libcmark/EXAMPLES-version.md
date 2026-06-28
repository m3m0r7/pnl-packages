# libcmark version

Query the linked cmark library version, both as the packed integer and as the human-readable string.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcmark\Libcmark;

// Query the linked cmark library version (distinct from markdown_to_html).
$num = Libcmark::cmark_version();
echo 'cmark_version (packed int): ' . (is_object($num) ? $num->toInt() : $num) . "\n";

$str = Libcmark::cmark_version_string();
echo 'cmark_version_string: ' . (string) $str . "\n";
```
