        # libenet Package

        Package: `libenet/libenet`

        Base library: enet

        License: MIT

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libenet
        ```

        The package requires enet headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libenet\Libenet;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libenet = $runtime->load(Libenet::class);

// enet_initialize() must be called once before any other ENet call.
if ($libenet->enet_initialize() !== 0) {
    throw new \RuntimeException('ENet failed to initialise');
}

// enet_linked_version() returns the runtime ENetVersion.
$version = $libenet->enet_linked_version();
echo "ENet version code: $version\n";
$libenet->enet_deinitialize();

// Explore further: enet_host_create(), enet_host_connect(),
// enet_host_service(), enet_packet_create(), ...
        ```

        This snippet is printed when `pnl install libenet` finishes — it comes from the package's `examples` field in `pnlx.json`.
