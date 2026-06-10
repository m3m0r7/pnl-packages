# libgumbo/libgumbo examples

```php
use Pnlx\Libgumbo\Libgumbo;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libgumbo = $runtime->load(Libgumbo::class);

$html = '<html><body><h1>Hello, Gumbo!</h1></body></html>';

// gumbo_parse returns a GumboOutput* struct with a root GumboNode*
$output = $libgumbo->gumbo_parse($html);
if (!is_null($output)) {
    $root = $output->root;
    echo "Root node type: " . $root->type . "\n";
    $libgumbo->gumbo_destroy_output($output);
}
```
