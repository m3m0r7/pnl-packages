# Gumbo Package

Package: `libgumbo/libgumbo`

Base library: Gumbo

License: Apache-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libgumbo
```

The package requires Gumbo headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install libgumbo` finishes — it comes from the package's `examples` field in `pnlx.json`.
