# Lua Package

Package: `liblua/liblua`

Base library: Lua

License: MIT

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/liblua
```

The package requires Lua headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

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

This snippet is printed when `pnl install liblua` finishes — it comes from the package's `examples` field in `pnlx.json`.
