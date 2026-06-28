# libmosquitto/libmosquitto error and topic helpers

Resolve libmosquitto error and CONNACK codes to human-readable strings and validate a publish topic, without opening any network connection.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmosquitto\Libmosquitto;

// Translate a libmosquitto error code into a human-readable string.
echo (string) Libmosquitto::mosquitto_strerror(0) . PHP_EOL;
// Describe a broker CONNACK return code.
echo (string) Libmosquitto::mosquitto_connack_string(0) . PHP_EOL;
// Validate a publish topic (0 == MOSQ_ERR_SUCCESS).
$rc = Libmosquitto::mosquitto_pub_topic_check('test/topic');
echo (is_object($rc) ? $rc->toInt() : $rc) . PHP_EOL;
```
