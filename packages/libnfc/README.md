# libnfc Package

Package: `libnfc/libnfc`

Base library: libnfc

License: LGPL-3.0-or-later

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libnfc
```

The package requires libnfc headers such as `nfc/nfc.h`. It sets `symbol_prefix` to `nfc` because the library key is `libnfc` while exported functions use the `nfc_*` prefix.
