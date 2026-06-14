# libyajl/libyajl examples

```php
use Pnlx\Libyajl\Libyajl;

// Build a tiny JSON document with the streaming generator.
$gen = Libyajl::yajl_gen_alloc(null);
Libyajl::yajl_gen_integer($gen, 42);
Libyajl::yajl_gen_free($gen);

// Explore further: yajl_alloc(), yajl_parse(), yajl_complete_parse(),
// yajl_gen_get_buf(), yajl_gen_map_open(), ...
```
