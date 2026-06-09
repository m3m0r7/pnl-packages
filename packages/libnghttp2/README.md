# nghttp2 Package

Package: `libnghttp2/libnghttp2`

Base library: nghttp2

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnghttp2
```

The package requires nghttp2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libnghttp2\Libnghttp2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libnghttp2 = $runtime->load(Libnghttp2::class);

// nghttp2_version() returns a pointer to a nghttp2_info struct
$info = $libnghttp2->nghttp2_version(0);
echo "nghttp2 version: " . $info->version_str . "\n";
echo "Protocol: "       . $info->proto_str    . "\n";

// Validate an HTTP/2 header name (returns int 1 = valid, 0 = invalid)
$valid = $libnghttp2->nghttp2_check_header_name('content-type', strlen('content-type'));
echo "Header valid: $valid\n";
// ... use nghttp2_session_client_new() to start an HTTP/2 session ...
```

This snippet is printed when `pnl install libnghttp2` finishes — it comes from the package's `examples` field in `pnlx.json`.
