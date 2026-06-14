# libpcap/libpcap examples

```php
use Pnlx\Libpcap\Libpcap;
use function Pnlx\Util\is_null;

// Query the library version string (char* → PHP string)
$version = Libpcap::pcap_lib_version();
echo "libpcap version: $version\n";

// Look up the default network device for capture
$errbuf = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);
$handle = Libpcap::pcap_open_live('eth0', 65535, 1, 1000, $errbuf);
if (is_null($handle)) {
    echo "Could not open device\n";
} else {
    // ... capture packets with pcap_loop() / pcap_next() ...
    Libpcap::pcap_close($handle);
}
```
