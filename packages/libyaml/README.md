# libyaml Package

Package: `libyaml/libyaml`

Base library: libyaml

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libyaml
```

The package requires libyaml headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libyaml\Libyaml;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libyaml = $runtime->load(Libyaml::class);

// yaml_get_version_string() returns the libyaml version, e.g. "0.2.5".
$version = $libyaml->yaml_get_version_string();
echo "libyaml version: $version\n";

// Explore further: yaml_parser_initialize(), yaml_parser_set_input_string(),
// yaml_parser_parse(), yaml_parser_delete(), yaml_emitter_initialize(), ...
```

This snippet is printed when `pnl install libyaml` finishes — it comes from the package's `examples` field in `pnlx.json`.
