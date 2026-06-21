# MeCab Package

Package: `libmecab/libmecab`

Base library: MeCab (Japanese morphological analyzer)

License: BSD-3-Clause

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libmecab
```

The package requires the MeCab headers, the `libmecab` shared library, and a
system dictionary (e.g. `mecab-ipadic`) to be available through the system,
Homebrew, or configured search paths.

## PHP usage

```php
use Pnlx\Libmecab\Libmecab;

echo Libmecab::mecab_version() . PHP_EOL;

$mecab = Libmecab::mecab_new2('');
echo Libmecab::mecab_sparse_tostr($mecab, '日本語の形態素解析');
Libmecab::mecab_destroy($mecab);
```

This snippet is printed when `pnl install libmecab` finishes — it comes from the
package's `examples` field in `pnlx.json`.
