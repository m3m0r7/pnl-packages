# libspeex/libspeex examples

```php
use Pnlx\Libspeex\Libspeex;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libspeex = $runtime->load(Libspeex::class);

// Create a narrowband encoder (SPEEX_MODEID_NB = 0) and free it.
$mode = $libspeex->speex_lib_get_mode(0);
$encoder = $libspeex->speex_encoder_init($mode);
$libspeex->speex_encoder_destroy($encoder);

// Explore further: speex_bits_init(), speex_encode_int(),
// speex_decoder_init(), speex_decode_int(), ...
```
