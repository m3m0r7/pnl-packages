# libcap/libcap examples

```php
use Pnlx\Libcap\Libcap;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libcap = $runtime->load(Libcap::class);

// cap_init() allocates an empty capability set; cap_free() releases it.
$caps = $libcap->cap_init();
$libcap->cap_free($caps);

// Explore further: cap_get_proc(), cap_set_flag(),
// cap_set_proc(), cap_to_text(), ...
```
