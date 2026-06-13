# libglib2/libglib2 examples

```php
use Pnlx\Libglib2\Libglib2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libglib2 = $runtime->load(Libglib2::class);

// g_get_num_processors() returns the CPU count GLib sees.
$cpus = $libglib2->g_get_num_processors();
echo "GLib sees $cpus CPU(s)\n";

// Explore further: g_strdup(), g_hash_table_new(),
// g_list_append(), g_main_loop_new(), ...
```
