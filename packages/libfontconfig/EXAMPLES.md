# libfontconfig/libfontconfig examples

```php
use Pnlx\Libfontconfig\Libfontconfig;

// FcGetVersion() returns the runtime version, e.g. 21500 for 2.15.0.
$version = Libfontconfig::FcGetVersion();
echo "fontconfig version: $version\n";

// Initialise the default configuration.
Libfontconfig::FcInit();

// Explore further: FcConfigGetCurrent(), FcPatternCreate(),
// FcNameParse(), FcFontList(), FcFontMatch(), ...
```
