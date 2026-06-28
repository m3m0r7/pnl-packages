# libmecab/libmecab N-best parsing

`mecab_nbest_sparse_tostr()` returns the N most likely segmentations of a sentence at once (here the top 2), each as a TSV lattice terminated by `EOS`, instead of only the single best parse from `mecab_sparse_tostr()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libmecab\Libmecab;

$mecab = Libmecab::mecab_new2('');
if ($mecab === null) {
    throw new \RuntimeException('mecab_new2 failed: dictionary not found');
}
echo Libmecab::mecab_nbest_sparse_tostr($mecab, 2, '日本語');
Libmecab::mecab_destroy($mecab);
```
