# liblua/liblua examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liblua\Liblua;

$L = Liblua::luaL_newstate();
// luaL_openlibs is a function-like macro in modern Lua (it expands to
// luaL_openselectedlibs), so pnl surfaces it as a free function, not a method.
\Pnlx\Func\Liblua\luaL_openlibs($L);

// luaL_dostring() is a macro; use the real luaL_loadstring + lua_pcallk (= lua_pcall).
if (Liblua::luaL_loadstring($L, 'return 7 * 6')->toInt() === 0) { // LUA_OK
    Liblua::lua_pcallk($L, 0, 1, 0, 0, null);
    $isnum = 0;
    $answer = Liblua::lua_tointegerx($L, -1, $isnum);
    echo "lua: 7 * 6 = {$answer}\n";
}

Liblua::lua_close($L);
```
