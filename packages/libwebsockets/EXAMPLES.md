# libwebsockets/libwebsockets examples

```php
use Pnlx\Libwebsockets\Libwebsockets;

$libwebsockets = new Libwebsockets();

// lws_get_library_version() returns the version string, e.g. "4.3.3".
$version = $libwebsockets->lws_get_library_version();
echo "libwebsockets version: $version\n";

// Explore further: lws_create_context(), lws_client_connect_via_info(),
// lws_service(), lws_context_destroy(), ...
```
