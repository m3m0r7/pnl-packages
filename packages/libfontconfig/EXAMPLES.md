# libfontconfig/libfontconfig examples

```php
use Pnlx\Libfontconfig\Libfontconfig;

$libfontconfig = new Libfontconfig();

// FcGetVersion() returns the runtime version, e.g. 21500 for 2.15.0.
$version = $libfontconfig->FcGetVersion();
echo "fontconfig version: $version\n";

// Initialise the default configuration.
$libfontconfig->FcInit();

// Explore further: FcConfigGetCurrent(), FcPatternCreate(),
// FcNameParse(), FcFontList(), FcFontMatch(), ...
```
