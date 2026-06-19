# libwebsockets/libwebsockets examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libwebsockets\Libwebsockets;

// lws_get_library_version() returns the version string, e.g. "4.3.3".
$version = Libwebsockets::lws_get_library_version();
echo "libwebsockets version: $version\n";

// Explore further: lws_create_context(), lws_client_connect_via_info(),
// lws_service(), lws_context_destroy(), ...
```
