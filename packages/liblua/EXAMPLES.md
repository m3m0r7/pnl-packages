# liblua/liblua examples

```php
use Pnlx\Liblua\Liblua;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$liblua = $runtime->load(Liblua::class);

// Create a Lua state, execute a snippet, then close the state.
$L = $liblua->luaL_newstate();
if (is_null($L)) {
    throw new \RuntimeException('Failed to create Lua state');
}
$liblua->luaL_openlibs($L);
$liblua->luaL_dostring($L, 'print("Hello from Lua!")');
$liblua->lua_close($L);
```
