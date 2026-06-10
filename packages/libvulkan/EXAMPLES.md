# libvulkan/libvulkan examples

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
