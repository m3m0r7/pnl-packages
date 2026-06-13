# libpango/libpango examples

```php
use Pnlx\Libpango\Libpango;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libpango = $runtime->load(Libpango::class);

// pango_version_string() returns the Pango version, e.g. "1.52.0".
$version = $libpango->pango_version_string();
echo "Pango: $version\n";

// Explore further: pango_font_description_new(), pango_layout_new(),
// pango_layout_set_text(), pango_cairo_show_layout(), ...
```
