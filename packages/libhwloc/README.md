# hwloc Package

Package: `libhwloc/libhwloc`

Base library: hwloc

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libhwloc
```

The package requires the hwloc headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libhwloc\Libhwloc;

// hwloc_get_api_version() returns the ABI version as a packed 0xMMmmpp integer.
printf("hwloc API 0x%06x\n", Libhwloc::hwloc_get_api_version());
```

This snippet is printed when `pnl install libhwloc` finishes — it comes from the
package's `examples` field in `pnlx.json`.
