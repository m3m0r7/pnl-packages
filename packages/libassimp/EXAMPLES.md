# libassimp/libassimp examples

```php
use Pnlx\Libassimp\Libassimp;

$libassimp = new Libassimp();

// aiGetVersionMajor()/aiGetVersionMinor() report the Assimp version.
$major = $libassimp->aiGetVersionMajor();
$minor = $libassimp->aiGetVersionMinor();
echo "Assimp: $major.$minor\n";

// Explore further: aiImportFile(), aiApplyPostProcessing(),
// aiReleaseImport(), aiGetErrorString(), ...
```
