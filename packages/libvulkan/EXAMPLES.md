# libvulkan/libvulkan examples

```php
use Pnlx\Libvulkan\Libvulkan;

// vkEnumerateInstanceVersion writes the loader's API version through a uint32* out-param.
$version = 0;
Libvulkan::vkEnumerateInstanceVersion($version);
printf("Vulkan %d.%d.%d\n", ($version >> 22) & 0x7f, ($version >> 12) & 0x3ff, $version & 0xfff);
```
