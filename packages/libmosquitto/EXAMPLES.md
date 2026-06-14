# libmosquitto/libmosquitto examples

```php
use Pnlx\Libmosquitto\Libmosquitto;
use function Pnlx\Util\is_null;

$libmosquitto = new Libmosquitto();

// Initialise the library, create a client, publish a message, then clean up.
$libmosquitto->mosquitto_lib_init();
$mosq = $libmosquitto->mosquitto_new('php-pnl-client', true, null);
if (is_null($mosq)) {
    throw new \RuntimeException('mosquitto_new failed');
}
if ($libmosquitto->mosquitto_connect($mosq, 'localhost', 1883, 60) === 0) {
    $msg = 'hello mqtt';
    $libmosquitto->mosquitto_publish($mosq, null, 'test/topic', strlen($msg), $msg, 0, false);
    $libmosquitto->mosquitto_disconnect($mosq);
}
$libmosquitto->mosquitto_destroy($mosq);
$libmosquitto->mosquitto_lib_cleanup();
```
