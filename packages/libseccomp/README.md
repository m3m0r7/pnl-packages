        # libseccomp Package

        Package: `libseccomp/libseccomp`

        Base library: libseccomp

        License: LGPL-2.1-only

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libseccomp
        ```

        The package requires libseccomp headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

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

        This snippet is printed when `pnl install libseccomp` finishes — it comes from the package's `examples` field in `pnlx.json`.
