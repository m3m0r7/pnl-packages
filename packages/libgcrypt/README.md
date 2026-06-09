# Libgcrypt Package

Package: `libgcrypt/libgcrypt`

Base library: Libgcrypt

License: LGPL-2.1-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libgcrypt
```

The package requires Libgcrypt headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libgcrypt\Libgcrypt;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libgcrypt = $runtime->load(Libgcrypt::class);

// Check the runtime version (returns null if requirement not met).
$version = $libgcrypt->gcry_check_version(null);
echo "libgcrypt version: " . $version . PHP_EOL;

// Hash a string with SHA-256.
// GCRY_MD_SHA256 = 8, GCRY_MD_FLAG_SECURE = 2
$allocator = $runtime->allocator();
$hd = $allocator->make(\Pnlx\FFI\AllocationType::VoidPointer);
$libgcrypt->gcry_md_open($hd, 8, 0);
$data = "Hello, world!";
$libgcrypt->gcry_md_write($hd->cdata, $data, strlen($data));
$libgcrypt->gcry_md_final($hd->cdata);
// gcry_md_read(hd, algo) returns a pointer to the digest buffer.
$libgcrypt->gcry_md_close($hd->cdata);
echo "SHA-256 hash computed." . PHP_EOL;
```

This snippet is printed when `pnl install libgcrypt` finishes — it comes from the package's `examples` field in `pnlx.json`.
