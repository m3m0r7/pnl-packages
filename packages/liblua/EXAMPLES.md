# liblua/liblua examples

```php
use Pnlx\Liblua\Liblua;
use function Pnlx\Util\is_null;

// Create a Lua state, execute a snippet, then close the state.
$L = Liblua::luaL_newstate();
if (is_null($L)) {
    throw new \RuntimeException('Failed to create Lua state');
}
Liblua::luaL_openlibs($L);
Liblua::luaL_dostring($L, 'print("Hello from Lua!")');
Liblua::lua_close($L);
```
