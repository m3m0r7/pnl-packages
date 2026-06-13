        # libvips Package

        Package: `libvips/libvips`

        Base library: vips

        License: LGPL-2.1-or-later

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libvips
        ```

        The package requires vips headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libvips\Libvips;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libvips = $runtime->load(Libvips::class);

// vips_init(argv0) must run once before any other vips call.
$libvips->vips_init('pnl');
$major = $libvips->vips_version(0);
echo "libvips major: $major\n";
$libvips->vips_shutdown();

// Explore further: vips_image_new_from_file(), vips_resize(),
// vips_thumbnail(), vips_image_write_to_file(), ...
        ```

        This snippet is printed when `pnl install libvips` finishes — it comes from the package's `examples` field in `pnlx.json`.
