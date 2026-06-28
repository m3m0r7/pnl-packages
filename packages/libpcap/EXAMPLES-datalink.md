# libpcap link-layer type lookups

libpcap can translate link-layer (DLT_*) type codes into names and descriptions, and turn status/warning codes into readable messages, all without opening a capture device.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libpcap\Libpcap;

// Translate a link-layer type (DLT_*) into its short name and human
// description without opening any device.
$dlt = 1; // DLT_EN10MB
echo (string) Libpcap::pcap_datalink_val_to_name($dlt) . PHP_EOL;        // EN10MB
echo (string) Libpcap::pcap_datalink_val_to_description($dlt) . PHP_EOL; // Ethernet

// pcap_statustostr() turns a libpcap status/warning code into a message.
echo (string) Libpcap::pcap_statustostr(1) . PHP_EOL; // Generic warning
```
