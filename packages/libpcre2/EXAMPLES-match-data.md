# libpcre2/libpcre2 match-data allocation example

Allocate a PCRE2 match-data block and read back how many ovector pairs it holds, without compiling a pattern.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpcre2\Libpcre2;

// Allocate a match-data block sized for 10 ovector pairs (no compiled pattern
// required), then read the pair count back with pcre2_get_ovector_count_8().
$md = Libpcre2::pcre2_match_data_create_8(10, null);
$count = Libpcre2::pcre2_get_ovector_count_8($md);
echo "ovector pairs: " . (is_object($count) ? $count->toInt() : $count) . "\n";
Libpcre2::pcre2_match_data_free_8($md);
```
