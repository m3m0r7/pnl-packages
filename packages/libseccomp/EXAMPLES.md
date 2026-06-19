# libseccomp/libseccomp examples

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libseccomp\Libseccomp;

// Build a filter that allows all syscalls by default (SCMP_ACT_ALLOW).
$ctx = Libseccomp::seccomp_init(0x7fff0000);
Libseccomp::seccomp_release($ctx);

// Explore further: seccomp_rule_add(), seccomp_load(),
// seccomp_arch_add(), seccomp_export_bpf(), ...
```
