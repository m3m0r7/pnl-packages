# libnghttp2/libnghttp2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libnghttp2\Libnghttp2;

// nghttp2_check_header_name() validates an HTTP/2 header name (1 = valid, 0 = not).
$name = 'content-type';
echo 'content-type valid: ' . Libnghttp2::nghttp2_check_header_name($name, strlen($name)) . "\n"; // 1

$bad = 'Bad Header';
echo 'Bad Header valid: '  . Libnghttp2::nghttp2_check_header_name($bad, strlen($bad)) . "\n";   // 0

// nghttp2_check_authority() and nghttp2_session_client_new() build on the same API.
```
