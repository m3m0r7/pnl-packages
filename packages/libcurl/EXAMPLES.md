# libcurl/libcurl examples

```php
use Pnlx\Libcurl\Libcurl;
use function Pnlx\Util\is_null;

$libcurl = new Libcurl();

// Perform a simple GET request and print the response body
$libcurl->curl_global_init(3); // CURL_GLOBAL_ALL
$handle = $libcurl->curl_easy_init();
if (is_null($handle)) {
    throw new \RuntimeException('curl_easy_init failed');
}
$libcurl->curl_easy_setopt($handle, 10002, 'https://example.com'); // CURLOPT_URL
$libcurl->curl_easy_setopt($handle, 64,    1);                      // CURLOPT_FOLLOWLOCATION
$rc = $libcurl->curl_easy_perform($handle);
if ($rc !== 0) {
    echo 'curl error: ' . $libcurl->curl_easy_strerror($rc) . "\n";
}
$libcurl->curl_easy_cleanup($handle);
$libcurl->curl_global_cleanup();
```
