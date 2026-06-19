# libpng/libpng examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpng\Libpng;
use function Pnlx\Util\is_null;

// Print the runtime libpng version string
$versionNum = Libpng::png_access_version_number();
echo "libpng version number: {$versionNum}\n"; // e.g. 10643

// Create the read + info structs that every decode needs. The version string
// must match the headers libpng was built with.
$png = Libpng::png_create_read_struct('1.6.43', null, null, null);
if (is_null($png)) {
    throw new \RuntimeException('png_create_read_struct failed');
}
$info = Libpng::png_create_info_struct($png);
if (is_null($info)) {
    throw new \RuntimeException('png_create_info_struct failed');
}
echo "libpng read context ready\n";

// A real decode would continue with png_init_io()/png_read_info() and then read
// dimensions, e.g.:
// Libpng::png_init_io($png, $fp);
// Libpng::png_read_info($png, $info);
// $width  = Libpng::png_get_image_width($png, $info);
//
// png_destroy_read_struct() takes png_structpp/png_infopp (pointer-to-pointer)
// out-parameters, so cleanup needs allocated pointer holders rather than the
// values directly; the OS reclaims the structs at process exit here.
```
