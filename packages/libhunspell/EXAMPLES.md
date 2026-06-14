# libhunspell/libhunspell examples

```php
use Pnlx\Libhunspell\Libhunspell;

$libhunspell = new Libhunspell();

// Create a Hunspell handle from an affix + dictionary pair, then free it.
$handle = $libhunspell->Hunspell_create('en_US.aff', 'en_US.dic');
$libhunspell->Hunspell_destroy($handle);

// Explore further: Hunspell_spell(), Hunspell_suggest(),
// Hunspell_analyze(), Hunspell_free_list(), ...
```
