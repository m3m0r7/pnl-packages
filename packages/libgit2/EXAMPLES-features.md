# libgit2/libgit2 build features

Query the library's compiled-in capabilities via `git_libgit2_features()` (a bitmask) and check the build channel with `git_libgit2_prerelease()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libgit2\Libgit2;

// Initialize the library; the return value is the current init reference count.
$count = Libgit2::git_libgit2_init();
echo 'init count: ', (is_object($count) ? $count->toInt() : $count), "\n";

// git_libgit2_features() returns a bitmask of compiled-in capabilities.
$features = Libgit2::git_libgit2_features();
$features = is_object($features) ? $features->toInt() : $features;

$flags = [
    'THREADS'    => 1,
    'HTTPS'      => 2,
    'SSH'        => 4,
    'NSEC'       => 8,
    'SHA1'       => 1024,
    'SHA256'     => 2048,
];
$enabled = [];
foreach ($flags as $name => $bit) {
    if (($features & $bit) !== 0) {
        $enabled[] = $name;
    }
}
echo 'features bitmask: ', $features, "\n";
echo 'enabled features: ', ($enabled ? implode(', ', $enabled) : '(none)'), "\n";

// git_libgit2_prerelease() returns the prerelease tag (e.g. "alpha") or null for a stable release.
$pre = Libgit2::git_libgit2_prerelease();
echo 'prerelease: ', ($pre === null ? '(stable release)' : $pre), "\n";

Libgit2::git_libgit2_shutdown();
```
