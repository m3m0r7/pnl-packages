# libsnappy/libsnappy validating a compressed buffer

Check whether a buffer is a well-formed Snappy stream without decompressing it, using the snappy_status enum result.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsnappy\Libsnappy;

// snappy_validate_compressed_buffer inspects a buffer and reports whether it is a
// well-formed Snappy stream, without decompressing it. It returns a snappy_status
// PHP enum: SNAPPY_OK (0) for valid data, SNAPPY_INVALID_INPUT (1) otherwise.

// The single byte 0x00 is the minimal valid Snappy stream (an empty payload).
$valid = "\x00";
$rc = Libsnappy::snappy_validate_compressed_buffer($valid, strlen($valid));
echo "Empty stream: {$rc->name}\n"; // SNAPPY_OK

// Arbitrary bytes are not a valid Snappy stream.
$garbage = 'this is not snappy-compressed data';
$rc = Libsnappy::snappy_validate_compressed_buffer($garbage, strlen($garbage));
echo "Garbage: {$rc->name}\n"; // SNAPPY_INVALID_INPUT
```
