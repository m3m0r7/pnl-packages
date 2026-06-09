# libxml2 Package

Package: `libxml2/libxml2`

Base library: libxml2

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libxml2
```

The package requires libxml2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libxml2\Libxml2;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libxml2 = $runtime->load(Libxml2::class);

// xmlReadMemory() parses an XML document held in a string buffer.
$xml = "<root><item>hello</item></root>";
$doc = $libxml2->xmlReadMemory($xml, strlen($xml), "doc.xml", null, 0);
if (is_null($doc)) {
    echo "Parse failed\n";
} else {
    echo "Parsed OK\n";
    $libxml2->xmlFreeDoc($doc);
}
$libxml2->xmlCleanupParser();
```

This snippet is printed when `pnl install libxml2` finishes — it comes from the package's `examples` field in `pnlx.json`.
