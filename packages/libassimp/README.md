        # libassimp Package

        Package: `libassimp/libassimp`

        Base library: assimp

        License: BSD-3-Clause

        Install with `pnl`:

        ```sh
        pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libassimp
        ```

        The package requires assimp headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

        ## PHP usage

        ```php
        use Pnlx\Libassimp\Libassimp;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libassimp = $runtime->load(Libassimp::class);

// aiGetVersionMajor()/aiGetVersionMinor() report the Assimp version.
$major = $libassimp->aiGetVersionMajor();
$minor = $libassimp->aiGetVersionMinor();
echo "Assimp: $major.$minor\n";

// Explore further: aiImportFile(), aiApplyPostProcessing(),
// aiReleaseImport(), aiGetErrorString(), ...
        ```

        This snippet is printed when `pnl install libassimp` finishes — it comes from the package's `examples` field in `pnlx.json`.
