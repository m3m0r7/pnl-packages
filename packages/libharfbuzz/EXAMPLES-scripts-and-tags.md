# libharfbuzz script, tag, and version helpers

Resolve a script to its writing direction, pack an OpenType table string into a 32-bit tag, and gate code on a minimum HarfBuzz version.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libharfbuzz\Libharfbuzz;

// Resolve a script tag, ask HarfBuzz for its writing direction, then name it.
$script = Libharfbuzz::hb_script_from_string('Arab', -1);
$dir = Libharfbuzz::hb_script_get_horizontal_direction($script);
echo "Arabic direction: " . (string)Libharfbuzz::hb_direction_to_string($dir) . "\n";

// Convert an OpenType table/feature string to its packed 32-bit tag.
$tag = Libharfbuzz::hb_tag_from_string('GSUB', -1);
echo "GSUB tag: " . (is_object($tag) ? $tag->toInt() : $tag) . "\n";

// Guard a code path on a minimum HarfBuzz version.
$ok = Libharfbuzz::hb_version_atleast(2, 0, 0);
$ok = is_object($ok) ? $ok->toInt() : $ok;
echo "HarfBuzz >= 2.0.0: " . ($ok ? 'yes' : 'no') . "\n";
```
