# libassimp/libassimp examples

```php
use Pnlx\Libassimp\Libassimp;

// aiGetVersionMajor()/aiGetVersionMinor() report the Assimp version.
$major = Libassimp::aiGetVersionMajor();
$minor = Libassimp::aiGetVersionMinor();
echo "Assimp: $major.$minor\n";

// Explore further: aiImportFile(), aiApplyPostProcessing(),
// aiReleaseImport(), aiGetErrorString(), ...
```
