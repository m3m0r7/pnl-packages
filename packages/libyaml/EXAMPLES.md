# libyaml/libyaml examples

```php
use Pnlx\Libyaml\Libyaml;

$libyaml = new Libyaml();

// yaml_get_version_string() returns the libyaml version, e.g. "0.2.5".
$version = $libyaml->yaml_get_version_string();
echo "libyaml version: $version\n";

// Explore further: yaml_parser_initialize(), yaml_parser_set_input_string(),
// yaml_parser_parse(), yaml_parser_delete(), yaml_emitter_initialize(), ...
```
