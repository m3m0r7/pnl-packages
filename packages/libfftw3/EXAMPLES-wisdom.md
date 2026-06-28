# libfftw3/libfftw3 — wisdom export and import

Inspect FFTW's accumulated planner "wisdom" with `fftw_export_wisdom_to_string()`, probe for a system-wide wisdom file via `fftw_import_system_wisdom()`, and clear it with `fftw_forget_wisdom()`.

```php
<?php
require_once __DIR__ . '/@pnlx/autoload.php';

use Pnlx\Libfftw3\Libfftw3;

// FFTW can persist tuned-plan "wisdom". With no plans created yet, exporting it
// returns the library's minimal wisdom preamble (its build identity).
// fftw_import_system_wisdom() reports whether a system-wide wisdom file was found
// (1 = yes, 0 = no), and fftw_forget_wisdom() clears any accumulated wisdom.
$wisdom = Libfftw3::fftw_export_wisdom_to_string();
$sys = Libfftw3::fftw_import_system_wisdom();

echo 'exported wisdom: ' . trim((string) $wisdom) . "\n";
echo 'system wisdom present: ' . (is_object($sys) ? $sys->toInt() : $sys) . "\n";

Libfftw3::fftw_forget_wisdom();
echo "wisdom forgotten." . PHP_EOL;
```
