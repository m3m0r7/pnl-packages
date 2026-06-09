# Expat Package

Package: `libexpat/libexpat`

Base library: Expat

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libexpat
```

The package requires Expat headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libexpat\Libexpat;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libexpat = $runtime->load(Libexpat::class);

// Query Expat's version string (e.g. "expat_2.6.2").
$version = $libexpat->XML_ExpatVersion();
echo "Expat version: " . $version . PHP_EOL;

// Create a parser, feed a small XML document, then free it.
$parser = $libexpat->XML_ParserCreate(null);
if (is_null($parser)) {
    throw new \RuntimeException('XML_ParserCreate failed');
}
$xml = '<root><child attr="hello">world</child></root>';
$libexpat->XML_Parse($parser, $xml, strlen($xml), 1);
$libexpat->XML_ParserFree($parser);
echo "Parsed successfully." . PHP_EOL;
```

This snippet is printed when `pnl install libexpat` finishes — it comes from the package's `examples` field in `pnlx.json`.
