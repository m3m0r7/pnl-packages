# libpcre2/libpcre2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpcre2\Libpcre2;

// PCRE2_CONFIG_VERSION (= 11) asks the library for its version string.
// Calling pcre2_config_8() with a NULL output buffer is the documented way to
// query how many bytes (code units) that string needs, including the trailing
// NUL. A positive result means the linked PCRE2 build answered successfully.
$versionLen = (int) (string) Libpcre2::pcre2_config_8(11 /* PCRE2_CONFIG_VERSION */, null);
echo "PCRE2 version buffer length: {$versionLen}\n";

// PCRE2_CONFIG_UNICODE_VERSION (= 10) works the same way for the Unicode
// (UCD) version string that PCRE2 was built against.
$unicodeLen = (int) (string) Libpcre2::pcre2_config_8(10 /* PCRE2_CONFIG_UNICODE_VERSION */, null);
echo "PCRE2 Unicode version buffer length: {$unicodeLen}\n";
```
