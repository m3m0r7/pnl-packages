# libuuid/libuuid examples

```php
use Pnlx\Libuuid\Libuuid;
use Pnlx\Types\UnsignedChar;

// uuid_t is `unsigned char[16]`. Allocate the 16-byte buffer and let libuuid fill
// it; it decays to the `unsigned char *` (uint8_t*) the API expects.
$uuid = UnsignedChar::alloc(16);
Libuuid::uuid_generate($uuid);

// uuid_unparse writes the 36-char text form into a `char *` buffer — a by-reference
// parameter. Pass a pre-sized string (37 bytes: 36 chars + NUL) and read it back.
$out = str_repeat("\0", 37);
Libuuid::uuid_unparse($uuid, $out);
echo rtrim($out, "\0") . PHP_EOL; // e.g. 1b4e28ba-2fa1-11d2-883f-0016d3cca427

// uuid_generate_random() and uuid_generate_time() select a specific variant.
```
