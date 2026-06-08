# libnfc Package

Package: `libnfc/libnfc`

Base library: libnfc

License: LGPL-3.0-or-later

Install from the repository root:

```sh
pnl install packages/libnfc
```

The package requires libnfc headers such as `nfc/nfc.h`. It sets `symbol_prefix` to `nfc` because the library key is `libnfc` while exported functions use the `nfc_*` prefix.
