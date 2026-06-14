# libcap/libcap examples

```php
use Pnlx\Libcap\Libcap;

// cap_init() allocates an empty capability set; cap_free() releases it.
$caps = Libcap::cap_init();
Libcap::cap_free($caps);

// Explore further: cap_get_proc(), cap_set_flag(),
// cap_set_proc(), cap_to_text(), ...
```
