# libpango/libpango examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpango\Libpango;

// pango_version_string() returns the Pango version, e.g. "1.52.0".
$version = Libpango::pango_version_string();
echo "Pango: $version\n";

// Explore further: pango_font_description_new(), pango_layout_new(),
// pango_layout_set_text(), pango_cairo_show_layout(), ...
```
