# libduktape/libduktape examples

```php
use Pnlx\Libduktape\Libduktape;

// duk_create_heap_default() is a macro for duk_create_heap(NULL, NULL, NULL, NULL, NULL).
$ctx = Libduktape::duk_create_heap(null, null, null, null, null);
echo $ctx !== null ? "duktape heap created\n" : "failed\n";
if ($ctx !== null) {
    Libduktape::duk_destroy_heap($ctx);
}
```
