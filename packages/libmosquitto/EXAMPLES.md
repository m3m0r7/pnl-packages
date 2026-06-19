# libmosquitto/libmosquitto examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmosquitto\Libmosquitto;
use function Pnlx\Util\is_null;

// Initialise the library, create a client, publish a message, then clean up.
Libmosquitto::mosquitto_lib_init();
$mosq = Libmosquitto::mosquitto_new('php-pnl-client', true, null);
if (is_null($mosq)) {
    throw new \RuntimeException('mosquitto_new failed');
}
if (Libmosquitto::mosquitto_connect($mosq, 'localhost', 1883, 60)->toInt() === 0) {
    $msg = 'hello mqtt';
    Libmosquitto::mosquitto_publish($mosq, null, 'test/topic', strlen($msg), $msg, 0, false);
    Libmosquitto::mosquitto_disconnect($mosq);
}
Libmosquitto::mosquitto_destroy($mosq);
Libmosquitto::mosquitto_lib_cleanup();
```
