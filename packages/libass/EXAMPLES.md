# libass/libass examples

```php
use Pnlx\Libass\Libass;

$libass = new Libass();

// Create an ass_library handle, then free it.
$library = $libass->ass_library_init();
$libass->ass_library_done($library);

// Explore further: ass_renderer_init(), ass_new_track(),
// ass_read_file(), ass_render_frame(), ...
```
