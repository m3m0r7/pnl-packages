# libpcap/libpcap examples

```php
use Pnlx\Libpcap\Libpcap;

echo Libpcap::pcap_lib_version() . "\n"; // e.g. "libpcap version 1.10.x"

// pcap_open_dead() builds a capture handle with no live device — useful for
// compiling/inspecting without root or an interface. Close it when done.
$pcap = Libpcap::pcap_open_dead(1 /* DLT_EN10MB */, 65535);
echo $pcap !== null ? "pcap handle created\n" : "failed\n";
if ($pcap !== null) {
    Libpcap::pcap_close($pcap);
}
```
