# libseccomp/libseccomp examples

```php
use Pnlx\Libseccomp\Libseccomp;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libseccomp = $runtime->load(Libseccomp::class);

// Build a filter that allows all syscalls by default (SCMP_ACT_ALLOW).
$ctx = $libseccomp->seccomp_init(0x7fff0000);
$libseccomp->seccomp_release($ctx);

// Explore further: seccomp_rule_add(), seccomp_load(),
// seccomp_arch_add(), seccomp_export_bpf(), ...
```
