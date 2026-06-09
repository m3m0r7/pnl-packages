# libcurl Package

Package: `libcurl/libcurl`

Base library: libcurl

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libcurl
```

The package requires libcurl headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libcurl\Libcurl;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libcurl = $runtime->load(Libcurl::class);

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

This snippet is printed when `pnl install libcurl` finishes — it comes from the package's `examples` field in `pnlx.json`.
