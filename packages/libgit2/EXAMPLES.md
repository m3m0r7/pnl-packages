# libgit2/libgit2 examples

```php
use Pnlx\Libgit2\Libgit2;
use Pnlx\Runtime;
use function Pnlx\Util\is_null;

$runtime = new Runtime(__DIR__);
$libgit2 = $runtime->load(Libgit2::class);

$libgit2->git_libgit2_init();

// Open an existing repository and read its HEAD reference
$repo = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
$rc = $libgit2->git_repository_open($repo, '/path/to/repo');
if ($rc === 0) {
    $ref = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);
    $libgit2->git_repository_head($ref, $repo[0]);
    echo "HEAD: " . $libgit2->git_reference_shorthand($ref[0]) . "\n";
    $libgit2->git_reference_free($ref[0]);
    $libgit2->git_repository_free($repo[0]);
}

$libgit2->git_libgit2_shutdown();
```
