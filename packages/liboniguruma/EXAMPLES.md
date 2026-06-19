# liboniguruma/liboniguruma examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liboniguruma\Liboniguruma;
use Pnlx\Liboniguruma\OnigDefaultSyntax;
use Pnlx\Liboniguruma\OnigSyntaxPerl;

// Library version (char* → PHP string)
echo 'Oniguruma version: ' . Liboniguruma::onig_version() . "\n"; // e.g. 6.9.10

// Encodings and syntaxes are exported global *variables* (not functions). Each is
// surfaced as a flat marker class — \Pnlx\Liboniguruma\OnigDefaultSyntax,
// \Pnlx\Liboniguruma\OnigEncodingUTF8, \Pnlx\Liboniguruma\OnigSyntaxPerl, ... — so
// you pass its ::class straight to a function and the dispatch resolves the marker
// to the real C global transparently.
echo 'default syntax options: '
    . sprintf('0x%x', Liboniguruma::onig_get_syntax_options(OnigDefaultSyntax::class)->toInt()) . "\n"; // 0x0
echo 'perl syntax options:    '
    . sprintf('0x%x', Liboniguruma::onig_get_syntax_options(OnigSyntaxPerl::class)->toInt()) . "\n";    // 0x8

// The same marker classes are what onig_new()'s encoding/syntax arguments take,
// e.g. ...->onig_new($reg, ..., OnigEncodingUTF8::class, OnigDefaultSyntax::class, ...).
```
