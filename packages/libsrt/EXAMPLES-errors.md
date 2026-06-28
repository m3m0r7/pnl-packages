# libsrt error and reject strings

Translate SRT error codes and connection rejection reasons into human-readable strings.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libsrt\Libsrt;

// srt_strerror() maps an SRT error code (and errno) to a human-readable message.
$msg = Libsrt::srt_strerror(0, 0);
echo 'code 0: ' . (string)$msg . "\n";

// srt_rejectreason_str() names a connection rejection reason code.
$reason = Libsrt::srt_rejectreason_str(0);
echo 'reject 0: ' . (string)$reason . "\n";
```
