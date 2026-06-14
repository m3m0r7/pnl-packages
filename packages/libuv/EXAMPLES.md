# libuv/libuv examples

```php
use Pnlx\Libuv\Libuv;
use function Pnlx\Util\is_null;

// Print the libuv version string and numeric version.
echo Libuv::uv_version_string() . PHP_EOL; // e.g. '1.48.0'
echo Libuv::uv_version() . PHP_EOL;        // packed int: major<<16|minor<<8|patch

// Get (or create) the default event loop and run it.
$loop = Libuv::uv_default_loop();
// Attach handles/requests to $loop here, then:
Libuv::uv_run($loop, 0 /* UV_RUN_DEFAULT */);
Libuv::uv_loop_close($loop);
```
