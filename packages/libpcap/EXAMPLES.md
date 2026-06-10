# libpcap/libpcap examples

```php
use Pnlx\Libpcap\Libpcap;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libpcap = $runtime->load(Libpcap::class);

// Query the library version string (char* → PHP string)
$version = $libpcap->pcap_lib_version();
echo "libpcap version: $version\n";

// Look up the default network device for capture
$errbuf = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$handle = $libpcap->pcap_open_live('eth0', 65535, 1, 1000, $errbuf);
if (is_null($handle)) {
    echo "Could not open device\n";
} else {
    // ... capture packets with pcap_loop() / pcap_next() ...
    $libpcap->pcap_close($handle);
}
```
