# Tesseract OCR Package

Package: `libtesseract/libtesseract`

Base library: Tesseract OCR

License: Apache-2.0

Install with `pnl`:

```sh
pnl install https://github.com/m3m0r7/pnl-packages/tree/main/packages/libtesseract
```

The package requires the Tesseract OCR headers and shared library to be available
through the system, Homebrew, pkg-config, or configured search paths.

## PHP usage

```php
use Pnlx\Libtesseract\Libtesseract;

// TessVersion() returns the Tesseract OCR engine version string.
echo Libtesseract::TessVersion() . PHP_EOL;
```

This snippet is printed when `pnl install libtesseract` finishes — it comes from the
package's `examples` field in `pnlx.json`.
