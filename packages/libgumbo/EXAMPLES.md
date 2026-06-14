# libgumbo/libgumbo examples

```php
use Pnlx\Libgumbo\Libgumbo;
use function Pnlx\Util\is_null;

$html = '<html><body><h1>Hello, Gumbo!</h1></body></html>';

// gumbo_parse returns a GumboOutput* struct with a root GumboNode*
$output = Libgumbo::gumbo_parse($html);
if (!is_null($output)) {
    $root = $output->root;
    echo "Root node type: " . $root->type . "\n";
    Libgumbo::gumbo_destroy_output($output);
}
```
