# libnettle/libnettle examples

```php
use Pnlx\Libnettle\Libnettle;

// nettle-meta.h exposes a registry of the hash algorithms compiled into the
// library. Look one up by name; the call returns a typed wrapper around the
// C `struct nettle_hash *` (or null when the name is unknown).
$sha256 = Libnettle::nettle_lookup_hash('sha256');

if ($sha256 === null) {
    echo "sha256 not available\n";
    return;
}

// Read the algorithm metadata straight off the underlying C struct.
$meta = $sha256->cdata();
printf(
    "%s: digest_size=%d block_size=%d\n",
    \FFI::string($meta->name),
    $meta->digest_size,
    $meta->block_size,
);

// The registry accessors enumerate every algorithm family the build ships.
$hashes = Libnettle::nettle_get_hashes();
echo $hashes !== null ? "hash registry loaded\n" : "no hashes\n";
```
