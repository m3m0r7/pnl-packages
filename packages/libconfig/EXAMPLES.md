# libconfig/libconfig examples

```php
use Pnlx\Libconfig\Libconfig;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libconfig = $runtime->load(Libconfig::class);

// Initialise a config_t, read a file, then release it.
$cfg = FFI::new('config_t'); // allocate a config_t
$libconfig->config_init(FFI::addr($cfg));
// $libconfig->config_read_file(FFI::addr($cfg), 'app.cfg');
$libconfig->config_destroy(FFI::addr($cfg));

// Explore further: config_read_file(), config_lookup(),
// config_lookup_string(), config_setting_get_int(), ...
```
