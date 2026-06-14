# libspeex/libspeex examples

```php
use Pnlx\Libspeex\Libspeex;

// Create a narrowband encoder (SPEEX_MODEID_NB = 0) and free it.
$mode = Libspeex::speex_lib_get_mode(0);
$encoder = Libspeex::speex_encoder_init($mode);
Libspeex::speex_encoder_destroy($encoder);

// Explore further: speex_bits_init(), speex_encode_int(),
// speex_decoder_init(), speex_decode_int(), ...
```
