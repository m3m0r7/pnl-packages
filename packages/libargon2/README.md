# Argon2 Package

Package: `libargon2/libargon2`

Base library: Argon2

License: Apache-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libargon2
```

The package requires Argon2 headers and library files to be available through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libargon2\Libargon2;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libargon2 = $runtime->load(Libargon2::class);

// Hash a password with Argon2id and verify it
// argon2id_hash_encoded writes into a caller-supplied buffer (char *encoded)
$password   = 'hunter2';
$salt       = 'somesalt12345678'; // 16 bytes
$encodedLen = 512;
$encodedBuf = $runtime->allocator()->make(\Pnlx\FFI\AllocationType::VoidPointer);

$rc = $libargon2->argon2id_hash_encoded(
    2,              // t_cost: iterations
    1 << 16,        // m_cost: memory (64 MiB)
    1,              // parallelism
    $password, strlen($password),
    $salt, strlen($salt),
    32,             // hash length in bytes
    $encodedBuf, $encodedLen
);
// ARGON2_OK == 0
echo $rc === 0 ? "hash ok\n" : 'error: ' . $libargon2->argon2_error_message($rc) . "\n";
// Verify: $libargon2->argon2id_verify($encodedBuf, $password, strlen($password))
```

This snippet is printed when `pnl install libargon2` finishes — it comes from the package's `examples` field in `pnlx.json`.
