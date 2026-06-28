# liboniguruma/liboniguruma runtime limits & copyright

Read the library's copyright banner and its default runtime limits via no-argument getters (`onig_copyright` returns a `char*` string; the limit getters return scalars).

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Liboniguruma\Liboniguruma;

// Copyright banner (const char* → PHP string)
$copyright = Liboniguruma::onig_copyright();
echo 'Copyright: ' . (string)$copyright . "\n"; // e.g. Oniguruma 6.9.10 : Copyright (C) ...

// Default regex compilation parse-depth limit (unsigned int)
$depth = Liboniguruma::onig_get_parse_depth_limit();
echo 'Parse depth limit: ' . (is_object($depth) ? $depth->toInt() : $depth) . "\n"; // 4096

// Maximum nesting level for subexp calls (int)
$nest = Liboniguruma::onig_get_subexp_call_max_nest_level();
echo 'Subexp call max nest level: ' . (is_object($nest) ? $nest->toInt() : $nest) . "\n"; // 20
```
