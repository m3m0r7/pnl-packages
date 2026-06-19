# libconfig/libconfig examples

```php
use Pnlx\Libconfig\Libconfig;
use Pnlx\Libconfig\Types\config_t;

// `config_t` is a package struct. Allocate one with `new config_t()` — it is
// created in libconfig's own FFI scope and decays to a `config_t *` when passed.
$cfg = new config_t();
Libconfig::config_init($cfg);

// Parse a small configuration from a string.
$rc = Libconfig::config_read_string($cfg, 'answer = 42; greeting = "hello";');
echo "config_read_string rc = $rc\n"; // 1 (CONFIG_TRUE)

// Look up an integer. The `int *value` out-parameter is written back by reference.
$answer = 0;
Libconfig::config_lookup_int($cfg, 'answer', $answer);
echo "answer = $answer\n"; // 42

Libconfig::config_destroy($cfg);

// Explore further: config_read_file(), config_lookup(),
// config_lookup_string(), config_setting_get_int(), ...
```
