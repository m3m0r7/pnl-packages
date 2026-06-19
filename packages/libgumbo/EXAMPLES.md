# libgumbo/libgumbo examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgumbo\Libgumbo;
use function Pnlx\Util\is_null;

$html = '<html><body><h1>Hello, Gumbo!</h1></body></html>';

// gumbo_parse() parses HTML into a GumboOutput tree (using gumbo's default options).
$output = Libgumbo::gumbo_parse($html);
echo is_null($output) ? "parse failed\n" : "parsed " . strlen($html) . " bytes of HTML\n";

// Free it with gumbo_destroy_output(options, output) — it takes the same options the
// parse used (the exported \Pnlx\Libgumbo\kGumboDefaultOptions marker) plus the tree.
if (!is_null($output)) {
    Libgumbo::gumbo_destroy_output(\Pnlx\Libgumbo\kGumboDefaultOptions::class, $output);
}
```
