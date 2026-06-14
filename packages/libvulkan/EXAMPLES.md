# libvulkan/libvulkan examples

```php
use Pnlx\Libvulkan\Libvulkan;

$libvulkan = new Libvulkan();

// vkEnumerateInstanceVersion() fills an out-parameter with the Vulkan
// instance version packed as (major<<22|minor<<12|patch).
$pApiVersion = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::Int);
$result = $libvulkan->vkEnumerateInstanceVersion($pApiVersion);
$ver = $pApiVersion[0];
echo sprintf("Vulkan %d.%d.%d (VkResult=%d)\n",
    ($ver >> 22) & 0x7f, ($ver >> 12) & 0x3ff, $ver & 0xfff, $result);

// Explore further: vkCreateInstance(), vkEnumeratePhysicalDevices(), ...
```
