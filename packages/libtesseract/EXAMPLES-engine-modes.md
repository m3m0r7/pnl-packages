# libtesseract engine and segmentation modes

Create a `TessBaseAPI` handle and read its default page-segmentation mode and OCR engine mode as int-backed enums before releasing it.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libtesseract\Libtesseract;

// Create a Tesseract API handle (no language data needed for these queries).
$api = Libtesseract::TessBaseAPICreate();

// TessBaseAPIGetPageSegMode() returns the current page-segmentation mode enum.
$psm = Libtesseract::TessBaseAPIGetPageSegMode($api);
echo "page seg mode: " . $psm->name . " (" . $psm->toInt() . ")\n";

// TessBaseAPIOem() returns the active OCR engine mode enum.
$oem = Libtesseract::TessBaseAPIOem($api);
echo "engine mode: " . $oem->name . " (" . $oem->toInt() . ")\n";

// Release the handle.
Libtesseract::TessBaseAPIDelete($api);
```
