# libcurl version and error strings

Query libcurl's own version string and translate a `CURLcode` result into a human-readable message without making any network request.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libcurl\Libcurl;

// Query libcurl's own version string and translate a result code to text.
echo 'libcurl version: ' . (string) Libcurl::curl_version() . "\n";

// CURLE_COULDNT_RESOLVE_HOST = 6
echo 'error 6: ' . (string) Libcurl::curl_easy_strerror(6) . "\n";
```
