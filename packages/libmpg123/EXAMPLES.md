# libmpg123/libmpg123 examples

```php
use Pnlx\Libmpg123\Libmpg123;
use function Pnlx\Util\is_null;

$libmpg123 = new Libmpg123();

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
