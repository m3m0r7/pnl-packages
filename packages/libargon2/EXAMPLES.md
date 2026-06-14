# libargon2/libargon2 examples

```php
use Pnlx\Libargon2\Libargon2;

$libargon2 = new Libargon2();

// Hash a password with Argon2id and verify it
// argon2id_hash_encoded writes into a caller-supplied buffer (char *encoded)
$password   = 'hunter2';
$salt       = 'somesalt12345678'; // 16 bytes
$encodedLen = 512;
$encodedBuf = (new \Pnlx\FFI\Allocator())->make(\Pnlx\FFI\AllocationType::VoidPointer);

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
