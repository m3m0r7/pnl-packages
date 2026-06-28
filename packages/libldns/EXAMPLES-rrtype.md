# libldns/libldns record-type lookups

`ldns_get_rr_type_by_name()` maps a DNS record-type name to its numeric type, and `ldns_get_errorstr_by_id()` turns a status code into a readable message.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libldns\Libldns;

foreach (['A', 'AAAA', 'MX', 'TXT'] as $name) {
    $t = Libldns::ldns_get_rr_type_by_name($name);
    echo "$name = " . (is_object($t) ? $t->toInt() : $t) . PHP_EOL;
}

$msg = Libldns::ldns_get_errorstr_by_id(0);
echo "status 0: " . (string)$msg . PHP_EOL;
```
