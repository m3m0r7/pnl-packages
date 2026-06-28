# libnghttp2/libnghttp2 error-code introspection

Translate nghttp2 library and HTTP/2 protocol error codes into human-readable messages and check whether a library error is fatal.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnghttp2\Libnghttp2;

// nghttp2_strerror() maps a library error code to a human-readable message.
$msg = Libnghttp2::nghttp2_strerror(-501); // NGHTTP2_ERR_INVALID_ARGUMENT
echo 'strerror(-501): ' . (string)$msg . "\n"; // Invalid argument

// nghttp2_http2_strerror() names an HTTP/2 protocol error code.
$proto = Libnghttp2::nghttp2_http2_strerror(1); // PROTOCOL_ERROR
echo 'http2_strerror(1): ' . (string)$proto . "\n"; // PROTOCOL_ERROR

// nghttp2_is_fatal() reports whether a library error code is unrecoverable.
$fatal = Libnghttp2::nghttp2_is_fatal(-501);
echo 'is_fatal(-501): ' . (is_object($fatal) ? $fatal->toInt() : $fatal) . "\n"; // 0
```
