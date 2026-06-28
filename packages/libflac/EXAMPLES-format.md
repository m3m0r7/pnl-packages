# libflac format validation

Validate sample rates and block sizes against the FLAC format rules without touching any audio data.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libflac\Libflac;

// FLAC__format_sample_rate_is_valid() checks whether a sample rate is encodable.
$ok = Libflac::FLAC__format_sample_rate_is_valid(44100);
$ok = is_object($ok) ? $ok->toInt() : $ok;
echo "44100 Hz valid: " . ($ok ? "yes" : "no") . PHP_EOL;

$ok = Libflac::FLAC__format_sample_rate_is_valid(99999999);
$ok = is_object($ok) ? $ok->toInt() : $ok;
echo "99999999 Hz valid: " . ($ok ? "yes" : "no") . PHP_EOL;

// FLAC__format_blocksize_is_subset() checks a block size against the streamable subset.
$sub = Libflac::FLAC__format_blocksize_is_subset(4096, 44100);
$sub = is_object($sub) ? $sub->toInt() : $sub;
echo "blocksize 4096 @ 44100 in streamable subset: " . ($sub ? "yes" : "no") . PHP_EOL;
```
