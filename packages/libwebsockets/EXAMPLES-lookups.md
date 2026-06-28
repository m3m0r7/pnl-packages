# libwebsockets enum-to-string lookups

`lws_ss_state_name()` and `lws_token_to_string()` translate libwebsockets' internal Secure Streams state codes and HTTP/WebSocket header token indices into readable strings.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libwebsockets\Libwebsockets;

// Both helpers turn internal libwebsockets enum codes into readable strings.
for ($state = 1; $state <= 3; $state++) {
    $name = Libwebsockets::lws_ss_state_name($state);
    echo "secure-stream state $state: " . (string) $name . "\n";
}

foreach ([0, 3, 5] as $token) {
    $text = Libwebsockets::lws_token_to_string($token);
    echo "header token $token: '" . (string) $text . "'\n";
}
```
