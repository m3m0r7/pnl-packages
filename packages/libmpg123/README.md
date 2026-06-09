# mpg123 Package

Package: `libmpg123/libmpg123`

Base library: mpg123

License: LGPL-2.1-only

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmpg123
```

The package requires mpg123 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmpg123\Libmpg123;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libmpg123 = $runtime->load(Libmpg123::class);

$libmpg123->mpg123_init();

// Open a handle for decoding; mpg123_new() returns a pointer
$handle = $libmpg123->mpg123_new(null, null);
if (is_null($handle)) {
    echo "Failed to create mpg123 handle\n";
} else {
    $libmpg123->mpg123_open($handle, 'audio.mp3');
    // ... decode with mpg123_read() ...
    $libmpg123->mpg123_close($handle);
    $libmpg123->mpg123_delete($handle);
}

$libmpg123->mpg123_exit();
```

This snippet is printed when `pnl install libmpg123` finishes — it comes from the package's `examples` field in `pnlx.json`.
