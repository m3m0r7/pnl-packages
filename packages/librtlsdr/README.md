# librtlsdr Package

Package: `librtlsdr/librtlsdr`

Base library: librtlsdr

License: GPL-2.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/librtlsdr
```

The package requires librtlsdr headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Librtlsdr\Librtlsdr;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$librtlsdr = $runtime->load(Librtlsdr::class);

// List all connected RTL-SDR devices
$count = $librtlsdr->rtlsdr_get_device_count();
echo "RTL-SDR devices found: {$count}\n";
for ($i = 0; $i < $count; $i++) {
    $name = $librtlsdr->rtlsdr_get_device_name($i);
    echo "  [{$i}] {$name}\n";
}

// Open the first device and tune to FM broadcast band
if ($count > 0) {
    $dev = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
    $librtlsdr->rtlsdr_open($dev, 0);
    $librtlsdr->rtlsdr_set_center_freq($dev[0], 98_000_000); // 98 MHz
    $librtlsdr->rtlsdr_set_sample_rate($dev[0], 2_048_000);  // 2.048 MS/s
    // $librtlsdr->rtlsdr_read_sync($dev[0], $buf, $len, $nRead)
    $librtlsdr->rtlsdr_close($dev[0]);
}
```

This snippet is printed when `pnl install librtlsdr` finishes — it comes from the package's `examples` field in `pnlx.json`.
