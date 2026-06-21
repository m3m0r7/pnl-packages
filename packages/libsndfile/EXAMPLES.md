# libsndfile/libsndfile examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsndfile\Libsndfile;
use function Pnlx\Util\is_null;

// Get the libsndfile version string.
$version = Libsndfile::sf_version_string();
echo $version . PHP_EOL;

// Opening a file needs an SF_INFO struct: allocate the generated wrapper
// (new \Pnlx\Libsndfile\Types\SF_INFO()) and pass it where sf_open wants it:
// $info = new \Pnlx\Libsndfile\Types\SF_INFO();
// $sndfile = Libsndfile::sf_open('/path/to/audio.wav', 0x10 /* SFM_READ */, $info);
// if (!is_null($sndfile)) { Libsndfile::sf_close($sndfile); }
```
