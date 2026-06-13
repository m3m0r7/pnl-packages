# libassimp/libassimp examples

```php
use Pnlx\Libassimp\Libassimp;
use Pnlx\Runtime;

$runtime = new Runtime(__DIR__);
$libassimp = $runtime->load(Libassimp::class);

// aiGetVersionMajor()/aiGetVersionMinor() report the Assimp version.
$major = $libassimp->aiGetVersionMajor();
$minor = $libassimp->aiGetVersionMinor();
echo "Assimp: $major.$minor\n";

// Explore further: aiImportFile(), aiApplyPostProcessing(),
// aiReleaseImport(), aiGetErrorString(), ...
```
