# libraw/libraw examples

```php
use Pnlx\Libraw\Libraw;

// libraw_init(0) creates a processing handle; libraw_close() frees it.
$handle = Libraw::libraw_init(0);
Libraw::libraw_close($handle);

// Explore further: libraw_open_file(), libraw_unpack(),
// libraw_dcraw_process(), libraw_dcraw_make_mem_image(), ...
```
