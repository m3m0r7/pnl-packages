# libass/libass examples

```php
use Pnlx\Libass\Libass;

// Create an ass_library handle, then free it.
$library = Libass::ass_library_init();
Libass::ass_library_done($library);

// Explore further: ass_renderer_init(), ass_new_track(),
// ass_read_file(), ass_render_frame(), ...
```
