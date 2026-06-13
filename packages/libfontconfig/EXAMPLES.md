# libfontconfig/libfontconfig examples

```php
use Pnlx\Libfontconfig\Libfontconfig;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libfontconfig = $runtime->load(Libfontconfig::class);

// FcGetVersion() returns the runtime version, e.g. 21500 for 2.15.0.
$version = $libfontconfig->FcGetVersion();
echo "fontconfig version: $version\n";

// Initialise the default configuration.
$libfontconfig->FcInit();

// Explore further: FcConfigGetCurrent(), FcPatternCreate(),
// FcNameParse(), FcFontList(), FcFontMatch(), ...
```
