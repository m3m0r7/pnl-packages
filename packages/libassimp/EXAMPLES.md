# libassimp/libassimp examples

```php
use Pnlx\Libassimp\Libassimp;

// How many import formats does this Assimp build support?
$formats = (int)(string)Libassimp::aiGetImportFormatCount();
echo "Assimp import formats: $formats\n";

// Is the Wavefront OBJ extension supported? (non-zero means yes)
$objSupported = (int)(string)Libassimp::aiIsExtensionSupported(".obj");
echo ".obj supported: " . ($objSupported ? "yes" : "no") . "\n";

// No import has run yet, so the error string is empty.
echo "Last error: '" . (string)Libassimp::aiGetErrorString() . "'\n";

// Explore further: aiImportFile(), aiApplyPostProcessing(),
// aiReleaseImport(), aiGetExtensionList(), ...
```
