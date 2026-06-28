# libduktape/libduktape evaluating JavaScript

Evaluate JavaScript expressions with `duk_eval_raw()` and read the result off the value stack with `duk_get_number()` / `duk_get_string()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libduktape\Libduktape;

$ctx = Libduktape::duk_create_heap(null, null, null, null, null);

// Flags used by the duk_eval_string() convenience macro:
// DUK_COMPILE_EVAL(8) | NOSOURCE(512) | STRLEN(1024) | NOFILENAME(2048).
$flags = 8 | 512 | 1024 | 2048;

// Evaluate a JavaScript expression and read the numeric result off the stack.
Libduktape::duk_eval_raw($ctx, '1 + 2 * 3', 0, $flags);
$num = Libduktape::duk_get_number($ctx, -1);
echo 'eval number: ' . (string) $num . PHP_EOL;
Libduktape::duk_pop($ctx);

// Evaluate an expression that produces a string.
Libduktape::duk_eval_raw($ctx, "'duktape ' + 'rocks'", 0, $flags);
$str = Libduktape::duk_get_string($ctx, -1);
echo 'eval string: ' . (string) $str . PHP_EOL;
Libduktape::duk_pop($ctx);

Libduktape::duk_destroy_heap($ctx);
```
