# libnghttp2/libnghttp2 examples

```php
use Pnlx\Libnghttp2\Libnghttp2;

// nghttp2_version() returns a pointer to a nghttp2_info struct
$info = Libnghttp2::nghttp2_version(0);
echo "nghttp2 version: " . $info->version_str . "\n";
echo "Protocol: "       . $info->proto_str    . "\n";

// Validate an HTTP/2 header name (returns int 1 = valid, 0 = invalid)
$valid = Libnghttp2::nghttp2_check_header_name('content-type', strlen('content-type'));
echo "Header valid: $valid\n";
// ... use nghttp2_session_client_new() to start an HTTP/2 session ...
```
