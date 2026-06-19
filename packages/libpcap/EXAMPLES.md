# libpcap/libpcap examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpcap\Libpcap;
use function Pnlx\Util\is_null;

echo Libpcap::pcap_lib_version() . "\n"; // e.g. "libpcap version 1.10.x"

// pcap_open_dead() builds a capture handle with no live device — useful for
// compiling/inspecting without root or an interface. Close it when done.
$pcap = Libpcap::pcap_open_dead(1 /* DLT_EN10MB */, 65535);
echo !is_null($pcap) ? "pcap handle created\n" : "failed\n";
if (!is_null($pcap)) {
    Libpcap::pcap_close($pcap);
}
```
