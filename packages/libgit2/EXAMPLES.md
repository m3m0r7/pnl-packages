# libgit2/libgit2 examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgit2\Libgit2;

Libgit2::git_libgit2_init();

// git_libgit2_version writes major/minor/rev through three int* out-parameters.
$major = 0; $minor = 0; $rev = 0;
Libgit2::git_libgit2_version($major, $minor, $rev);
echo "libgit2 {$major}.{$minor}.{$rev}\n";

Libgit2::git_libgit2_shutdown();
```
