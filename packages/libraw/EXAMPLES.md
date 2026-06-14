# libraw/libraw examples

```php
use Pnlx\Libraw\Libraw;

$libraw = new Libraw();

// libraw_init(0) creates a processing handle; libraw_close() frees it.
$handle = $libraw->libraw_init(0);
$libraw->libraw_close($handle);

// Explore further: libraw_open_file(), libraw_unpack(),
// libraw_dcraw_process(), libraw_dcraw_make_mem_image(), ...
```
