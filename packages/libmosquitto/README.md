# Mosquitto Package

Package: `libmosquitto/libmosquitto`

Base library: Mosquitto

License: EPL-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmosquitto
```

The package requires Mosquitto headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libmosquitto\Libmosquitto;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libmosquitto = $runtime->load(Libmosquitto::class);

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

This snippet is printed when `pnl install libmosquitto` finishes — it comes from the package's `examples` field in `pnlx.json`.
