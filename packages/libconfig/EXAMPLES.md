# libconfig/libconfig examples

```php
use Pnlx\Libconfig\Libconfig;

// Initialise a config_t, read a file, then release it.
$cfg = FFI::new('config_t'); // allocate a config_t
Libconfig::config_init(FFI::addr($cfg));
// Libconfig::config_read_file(FFI::addr($cfg), 'app.cfg');
Libconfig::config_destroy(FFI::addr($cfg));

// Explore further: config_read_file(), config_lookup(),
// config_lookup_string(), config_setting_get_int(), ...
```
