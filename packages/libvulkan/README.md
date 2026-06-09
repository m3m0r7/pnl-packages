# Vulkan Package

Package: `libvulkan/libvulkan`

Base library: Vulkan

License: Apache-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libvulkan
```

The package requires Vulkan headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libvulkan\Libvulkan;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libvulkan = $runtime->load(Libvulkan::class);

// vkEnumerateInstanceVersion() fills an out-parameter with the Vulkan
// instance version packed as (major<<22|minor<<12|patch).
$pApiVersion = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::Int);
$result = $libvulkan->vkEnumerateInstanceVersion($pApiVersion);
$ver = $pApiVersion[0];
echo sprintf("Vulkan %d.%d.%d (VkResult=%d)\n",
    ($ver >> 22) & 0x7f, ($ver >> 12) & 0x3ff, $ver & 0xfff, $result);

// Explore further: vkCreateInstance(), vkEnumeratePhysicalDevices(), ...
```

This snippet is printed when `pnl install libvulkan` finishes — it comes from the package's `examples` field in `pnlx.json`.
