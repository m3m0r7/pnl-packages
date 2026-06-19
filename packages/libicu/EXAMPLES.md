# libicu/libicu examples

```php
use Pnlx\Libicu\Libicu;

// ICU exports every entry point under a version-suffixed symbol (e.g.
// `u_errorName_74`) and ships `#define u_errorName …` so callers use the
// unversioned name. pnl recovers that rename, so the public name works directly.
echo "U_ZERO_ERROR             => " . Libicu::u_errorName(0) . "\n";
echo "U_ILLEGAL_ARGUMENT_ERROR => " . Libicu::u_errorName(1) . "\n";
echo "U_INDEX_OUTOFBOUNDS_ERROR=> " . Libicu::u_errorName(8) . "\n";
```
