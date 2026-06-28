# liblua/liblua version query

Read the Lua core version number with `lua_version`, which accepts a NULL state so no `lua_State` has to be created.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblua\Liblua;

// lua_version() reports the interpreter's core version number and accepts a
// NULL state, so no lua_State has to be created to query it. The number is
// encoded as major * 100 + minor (e.g. 504 = Lua 5.4, 505 = Lua 5.5).
$v = Liblua::lua_version(null);
$v = is_object($v) ? $v->toFloat() : (float) $v;
echo 'Lua core version number: ' . (int) $v . PHP_EOL; // e.g. "Lua core version number: 504"
```
