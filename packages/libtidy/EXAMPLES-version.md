# libtidy/libtidy version metadata

Read the libtidy build version and release date without creating a document handle.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtidy\Libtidy;

// Query libtidy build metadata; neither call needs a document handle.
$version = Libtidy::tidyLibraryVersion();
$date = Libtidy::tidyReleaseDate();
echo 'libtidy version: ' . (string) $version . "\n"; // e.g. "5.8.0"
echo 'release date: ' . (string) $date . "\n";       // e.g. "2021/07/10"
```
