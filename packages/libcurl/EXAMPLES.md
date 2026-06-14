# libcurl/libcurl examples

```php
use Pnlx\Libcurl\Libcurl;
use function Pnlx\Util\is_null;

// Perform a simple GET request and print the response body
Libcurl::curl_global_init(3); // CURL_GLOBAL_ALL
$handle = Libcurl::curl_easy_init();
if (is_null($handle)) {
    throw new \RuntimeException('curl_easy_init failed');
}
Libcurl::curl_easy_setopt($handle, 10002, 'https://example.com'); // CURLOPT_URL
Libcurl::curl_easy_setopt($handle, 64,    1);                      // CURLOPT_FOLLOWLOCATION
$rc = Libcurl::curl_easy_perform($handle);
if ($rc !== 0) {
    echo 'curl error: ' . Libcurl::curl_easy_strerror($rc) . "\n";
}
Libcurl::curl_easy_cleanup($handle);
Libcurl::curl_global_cleanup();
```
