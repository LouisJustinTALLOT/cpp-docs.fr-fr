---
title: Graphiques (C++ AMP)
ms.date: 11/04/2016
ms.assetid: 190a98a4-5f7d-442e-866b-b374ca74c16f
ms.openlocfilehash: 6e21c5af094ce90c8e4365ed4263198422ad1905
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449872"
---
# <a name="graphics-c-amp"></a>Graphiques (C++ AMP)

C++ AMP contient plusieurs API dans le [Concurrency::graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) espace de noms que vous pouvez utiliser pour accéder à la prise en charge de texture sur GPU. Voici quelques scénarios courants :

- Vous pouvez utiliser la [texture](../../parallel/amp/reference/texture-class.md) classe comme un conteneur de données pour le calcul et d’exploiter le *localité spatiale* du cache de texture et dispositions du matériel GPU. La localité spatiale est la propriété des éléments de données physiquement proches les uns des autres.

- Le runtime fournit une interopérabilité efficace avec des nuanceurs non calculés. Les pixels, les vertex, les pavages et les nuanceurs de coque consomment ou produisent fréquemment des textures utilisables dans les calculs C++ AMP.

- Les API graphiques de C++ AMP fournissent d'autres moyens pour accéder aux mémoires tampons contenant des sous-mots. Les textures formatées *texels* (éléments de texture) qui sont composées de 8 bits ou 16 bits scalaires autorisent l’accès à ce stockage de données compressées.

## <a name="the-norm-and-unorm-types"></a>Les types norm et unorm

Le `norm` et `unorm` types sont des types scalaires qui limitent la plage de **float** valeurs ; il s’agit *serrage*. Ces types peuvent être explicitement construits à partir d'autres types scalaires. Dans un casting, la valeur est premièrement transtypée en **float** , puis fixée à la zone respective autorisée par norm [-1.0, 1.0] ou unorm [0.0, 1.0]. Le cast de +/- infini retourne +/-1. Le cast depuis NaN n'est pas défini. Un norm peut être implicitement construit à partir d'un unorm sans perte de données. L'opérateur de conversion implicite en float est défini sur ces types. Opérateurs binaires sont définis entre ces types et les autres types scalaires intégrés tels que **float** et **int**: +, -, \*, /, ==, ! =, >, \<, > =, < =. Les opérateurs d’assignation composée sont également autorisés : +=, -=, \*=, / =. L'opérateur de négation unaire (-) est défini pour les types norm.

## <a name="short-vector-library"></a>Bibliothèque de vecteurs courts

La bibliothèque de vecteurs courts fournit certaines des fonctionnalités de la [Type vectoriel](https://go.microsoft.com/fwlink/p/?linkid=248500) qui est défini dans HLSL et est généralement utilisé pour définir des texels. Un vecteur court est une structure de données contenant une à quatre valeurs du même type. Les types pris en charge sont **double**, **float**, **int**, `norm`, `uint`, et `unorm`. Les noms des types sont affichés dans le tableau suivant. Pour chaque type, il existe également un correspondant **typedef** qui n’a pas un trait de soulignement dans le nom. Les types ayant les traits de soulignement sont dans le [Concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md). Les types qui n’ont pas les traits de soulignement sont dans le [Concurrency::Graphics :: Direct3D Namespace](../../parallel/amp/reference/concurrency-graphics-direct3d-namespace.md) afin qu’ils soient clairement séparés à partir des types fondamentaux portent des noms tels que **__int8** et **__int16**.

||Length 2|Longueur de 3|Longueur 4|
|-|--------------|--------------|--------------|
|double|double_2<br /><br /> double2|double_3<br /><br /> double3|double_4<br /><br /> double4|
|float|float_2<br /><br /> float2|float_3<br /><br /> float3|float_4<br /><br /> float4|
|int|int_2<br /><br /> int2|int_3<br /><br /> int3|int_4<br /><br /> int4|
|norm|norm_2<br /><br /> norm2|norm_3<br /><br /> norm3|norm_4<br /><br /> norm4|
|uint|uint_2<br /><br /> uint2|uint_3<br /><br /> uint3|uint_4<br /><br /> uint4|
|unorm|unorm_2<br /><br /> unorm2|unorm_3<br /><br /> unorm3|unorm_4<br /><br /> unorm4|

### <a name="operators"></a>Opérateurs

Si un opérateur est défini entre deux vecteurs courts, alors il est également défini entre un vecteur court et un scalaire. De plus, l'une d'elles doit avoir la valeur True :

- Le type du scalaire doit être identique au type d'élément du vecteur court.

- Le type du scalaire peut être implicitement converti vers le type d'élément du vecteur à l'aide d'une seule conversion définie par l'utilisateur.

L'opération est portée entre chaque composant du vecteur court et la variable scalaire. Voici les opérateurs valides :

|Type d'opérateur|Types valides|
|-------------------|-----------------|
|Opérateurs binaires|Valide sur tous les types : +, -, \*, /,<br /><br /> Valide sur les types d’entiers : %, ^, &#124;, &, <\<, >><br /><br /> Les deux vecteurs doivent avoir la même taille et le résultat doit être un vecteur de la même taille.|
|Opérateurs relationnels|Valides sur tous les types : == et !=|
|Opérateur d'assignation composée|Valide sur tous les types : +=, -=, \*=, / =<br /><br /> Valid on integer types: %=, ^=, &#124;=, &=, <\<=, >>=|
|Opérateurs d'incrémentation et de décrémentation|Valides sur tous les types : ++, --<br /><br /> Le préfixe et le suffixe sont valides.|
|Opérateur de bits Not (~)|Valide sur les types d'entiers.|
|Opérateur unaire|Valide sur tous les types hormis `unorm` et `uint`.|

### <a name="swizzling-expressions"></a>Expressions de swizzling

La bibliothèque de vecteurs courts prend en charge la construction de l'accesseur `vector_type.identifier` pour accéder aux composants d'un vecteur court. Le `identifier`, qui est appelé un *expression de swizzling*, spécifie les composants du vecteur. L'expression peut être une l-value ou une r-value. Les caractères individuels dans l’identificateur peuvent être : x, y, z et w ; ou r, g, b et un. « x » et « r » désigne le composant zéro, « y » et « g » désigne le premier composant et ainsi de suite. (Notez que « x » et « r » ne peuvent être utilisés dans le même identificateur.) Par conséquent, « rgba » et « xyzw » retournent le même résultat. Les accesseurs à un composant tels que « x » et « y » sont des types de valeur scalaire. Les accesseurs à plusieurs composants sont des types de vecteurs courts. Par exemple, si vous construisez un vecteur `int_4` nommé `fourInts` et ayant les valeurs 2, 4, 6 et 8, alors `fourInts.y` retourne l'entier 4 et `fourInts.rg` retourne un objet `int_2` ayant les valeurs 2 et 4.

## <a name="texture-classes"></a>Classes de texture

De nombreux GPU ont un matériel et des caches optimisées pour récupérer des pixels et des texels afin d'afficher des images et des textures. Le [texture\<T, N >](../../parallel/amp/reference/texture-class.md) (classe), qui est une classe de conteneur pour objets texel, expose les fonctionnalités de texture de ces GPU. Un texel peut être :

- Un **int**, `uint`, **float**, **double**, `norm`, ou `unorm` scalaire.

- Un vecteur court ayant deux ou quatre composants. La seule exception est `double_4`, qui n'est pas autorisée.

L'objet `texture` peut avoir un rang de 1, 2 ou 3. L'objet `texture` peut être capturé uniquement par référence dans le lambda d'un appel à `parallel_for_each`. La texture est stockée sur le GPU en tant qu'objet de texture Direct3D. Pour plus d’informations sur les textures et les texels dans Direct3D, consultez [Introduction aux Textures dans Direct3D 11](https://go.microsoft.com/fwlink/p/?linkid=248502).

Le type de texel que vous utilisez peut être l'un des nombreux formats de texture utilisés dans la programmation graphique. Par exemple, un format RVBA peut utiliser 32 bits, avec 8 bits pour chacun des éléments scalaires R, G, B et A. Le matériel de texture d'une carte graphique peut accéder à chaque élément selon son format. Par exemple, si vous utilisez le format RVBA, le matériel de texture peut extraire chaque élément de 8 bits dans une forme 32 bits. En C++ AMP, vous pouvez définir des bits par élément scalaire de votre texel afin d'accéder automatiquement aux éléments scalaires individuels dans le code sans utiliser le décalage de bits.

### <a name="instantiating-texture-objects"></a>Instanciation d'objets de texture

Vous pouvez déclarer un objet de texture sans l'initialiser. L'exemple de code suivant déclare plusieurs objets de texture.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextures() {
    // Create a 16-texel texture of int.
    texture<int, 1> intTexture1(16);
    texture<int, 1> intTexture2(extent<1>(16));

    // Create a 16 x 32 texture of float_2.
    texture<float_2, 2> floatTexture1(16, 32);
    texture<float_2, 2> floatTexture2(extent<2>(16, 32));

    // Create a 2 x 4 x 8 texture of uint_4.
    texture<uint_4, 3> uintTexture1(2, 4, 8);
    texture<uint_4, 3> uintTexture2(extent<3>(2, 4, 8));
}
```

Vous pouvez également utiliser un constructeur pour déclarer et initialiser un objet `texture`. L'exemple de code suivant instancie un objet `texture` à partir d'un vecteur d'objets `float_4`. Les bits par élément scalaire sont définis à la valeur par défaut. Vous ne pouvez pas utiliser ce constructeur avec `norm`, `unorm` ou les vecteurs courts de `norm` et de `unorm`, car ils n'ont pas de bits par défaut par élément scalaire.

```cpp
#include <amp.h>
#include <amp_graphics.h>
#include <vector>
using namespace concurrency;
using namespace concurrency::graphics;

void initializeTexture() {
    std::vector<int_4> texels;
    for (int i = 0; i < 768 * 1024; i++) {
        int_4 i4(i, i, i, i);
        texels.push_back(i4);
    }

    texture<int_4, 2> aTexture(768, 1024, texels.begin(), texels.end());
}
```

Vous pouvez également déclarer et initialiser un objet `texture` à l'aide d'une surcharge de constructeur renvoyant un pointeur vers les données sources, la taille en octets des données sources et les bits par élément scalaire.

```cpp
void createTextureWithBPC() { // Create the source data.
    float source[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        source[i] = (float)i;
    }
    // Initialize the texture by using the size of source in bytes // and bits per scalar element.
    texture<float_2, 1> floatTexture(1024, source, (unsigned int)sizeof(source), 32U);
}
```

Les textures dans ces exemples sont créées sur la vue par défaut de l'accélérateur par défaut. Vous pouvez utiliser d'autres surcharges du constructeur si vous souhaitez spécifier un objet `accelerator_view`. Vous ne pouvez pas créer un objet de texture sur un accélérateur CPU.

Il existe des limites sur la taille de chaque dimension de l'objet `texture`, comme l'indique le tableau suivant. Une erreur d'exécution est générée si vous dépassez les limites.

|Texture|Limite de taille par dimension|
|-------------|---------------------|
|texture\<T, 1 >|16384|
|texture\<T, 2 >|16384|
|texture\<T, 3 >|2048|

### <a name="reading-from-texture-objects"></a>Lecture des objets de texture

Vous pouvez lire à partir d’un `texture` objet à l’aide de [texture::operator\[\]](reference/texture-class.md#operator_at), [texture::operator opérateur](reference/texture-class.md#operator_call), ou [texture::Get, méthode](reference/texture-class.md#get). Les deux opérateurs retournent une valeur, pas une référence. Par conséquent, vous ne pouvez pas écrire dans un objet `texture` à l'aide de `texture::operator\[\]`.

```cpp
void readTexture() {
    std::vector<int_2> src;
    for (int i = 0; i <16 *32; i++) {
        int_2 i2(i, i);

        src.push_back(i2);
    }

    std::vector<int_2> dst(16* 32);

    array_view<int_2, 2> arr(16, 32, dst);

    arr.discard_data();

    const texture<int_2, 2> tex9(16, 32, src.begin(), src.end());

    parallel_for_each(tex9.extent, [=, &tex9] (index<2> idx) restrict(amp) { // Use the subscript operator.
        arr[idx].x += tex9[idx].x; // Use the function () operator.
        arr[idx].x += tex9(idx).x; // Use the get method.
        arr[idx].y += tex9.get(idx).y; // Use the function () operator.
        arr[idx].y += tex9(idx[0], idx[1]).y;
    });

    arr.synchronize();
}
```

L'exemple de code suivant montre comment inscrire des canaux de texture dans un vecteur court, puis comment accéder aux éléments scalaires individuels en tant que propriétés du vecteur court.

```cpp
void UseBitsPerScalarElement() { // Create the image data. // Each unsigned int (32-bit) represents four 8-bit scalar elements(r,g,b,a values).
    const int image_height = 16;
    const int image_width = 16;
    std::vector<unsigned int> image(image_height* image_width);

    extent<2> image_extent(image_height, image_width);

    // By using uint_4 and 8 bits per channel, each 8-bit channel in the data source is // stored in one 32-bit component of a uint_4.
    texture<uint_4, 2> image_texture(image_extent, image.data(), image_extent.size()* 4U,  8U);

    // Use can access the RGBA values of the source data by using swizzling expressions of the uint_4.
    parallel_for_each(image_extent,
        [&image_texture](index<2> idx) restrict(amp)
        { // 4 bytes are automatically extracted when reading.
            uint_4 color = image_texture[idx];
            unsigned int r = color.r;
            unsigned int g = color.g;
            unsigned int b = color.b;
            unsigned int a = color.a;
        });
}
```

Le tableau suivant répertorie les bits valides par canal pour chaque type de vecteur de tri.

|Type de données de texture|Bits valides par élément scalaire|
|-----------------------|-----------------------------------|
|int, int_2, int_4<br /><br /> uint, uint_2, uint_4|8, 16, 32|
|int_3, uint_3|32|
|float, float_2, float_4|16, 32|
|float_3|32|
|double, double_2|64|
|norm, norm_2, norm_4<br /><br /> unorm, unorm_2, unorm, 4|8, 16|

### <a name="writing-to-texture-objects"></a>Écrire dans des objets de texture

Utilisez le [texture::set](reference/texture-class.md#set) méthode pour écrire dans `texture` objets. Un objet de texture peut être accessible en lecture seule ou en lecture/écriture. Pour qu'un objet de texture soit lisible et accessible en écriture, les conditions suivantes doivent être remplies :

- T possède seulement un composant scalaire. (Les vecteurs courts ne sont pas autorisés.)

- T n’est pas **double**, `norm`, ou `unorm`.

- La propriété `texture::bits_per_scalar_element` est 32.

Si toutes trois ne sont pas vraies, l'objet `texture` est accessible en lecture seule. Les deux premières conditions sont vérifiées pendant la compilation. Une erreur de compilation est générée si votre code essaie d'écrire dans un objet de texture `readonly`. La condition pour `texture::bits_per_scalar_element` est détectée au moment de l’exécution, et le runtime génère le [unsupported_feature](../../parallel/amp/reference/unsupported-feature-class.md) exception si vous tentez d’écrire un ReadOnly `texture` objet.

L'exemple de code suivant écrit des valeurs dans un objet de texture.

```cpp
void writeTexture() {
    texture<int, 1> tex1(16);

    parallel_for_each(tex1.extent, [&tex1] (index<1> idx) restrict(amp) {
        tex1.set(idx, 0);
    });
}
```

### <a name="copying-texture-objects"></a>Copie d'objets de texture

Vous pouvez copier entre les objets de texture à l’aide de la [copie](reference/concurrency-namespace-functions-amp.md#copy) fonction ou le [copy_async](reference/concurrency-namespace-functions-amp.md#copy_async) de fonction, comme indiqué dans l’exemple de code suivant.

```cpp
void copyHostArrayToTexture() { // Copy from source array to texture object by using the copy function.
    float floatSource[1024* 2];
    for (int i = 0; i <1024* 2; i++) {
        floatSource[i] = (float)i;
    }
    texture<float_2, 1> floatTexture(1024);

    copy(floatSource, (unsigned int)sizeof(floatSource), floatTexture);

    // Copy from source array to texture object by using the copy function.
    char charSource[16* 16];
    for (int i = 0; i <16* 16; i++) {
        charSource[i] = (char)i;
    }
    texture<int, 2> charTexture(16, 16, 8U);

    copy(charSource, (unsigned int)sizeof(charSource), charTexture);
    // Copy from texture object to source array by using the copy function.
    copy(charTexture, charSource, (unsigned int)sizeof(charSource));
}
```

Vous pouvez également copier à partir d’une texture à un autre à l’aide de la [texture::copy_to](reference/texture-class.md#copy_to) (méthode). Les deux textures peuvent être sur des accelerator_views différents. Lorsque vous effectuez une copie vers un objet `writeonly_texture_view`, les données sont copiées dans l'objet `texture` sous-jacent. Les bits par élément scalaire et l'extent doivent être identiques sur les objets `texture` sources et de destination. Si ces exigences ne sont pas satisfaites, le runtime lève une exception.

## <a name="texture-view-classes"></a>Classes d'affichage de texture

C++AMP introduit le [texture_view, classe](../../parallel/amp/reference/texture-view-class.md) dans Visual Studio 2013. Les vues de texture prennent en charge les mêmes types de texel et rangs en tant que le [texture, classe](../../parallel/amp/reference/texture-class.md), mais contrairement aux textures, ils fournissent un accès à des fonctionnalités matérielles supplémentaires telles que l’échantillonnage de texture et les mipmaps. Les vues de texture prennent en charge l'accès en lecture seule, en écriture seule et en lecture-écriture aux données de texture sous-jacentes.

- L'accès en lecture seule est fourni par une spécialisation de modèle `texture_view<const T, N>`, qui prend en charge des éléments comportant 1, 2 ou 4 composants, un échantillonnage de texture et un accès dynamique à une plage de niveaux de mipmaps qui sont déterminés lorsque la vue est instanciée.

- L'accès en écriture seule est fournie par la classe de modèles non spécialisée `texture_view<T, N>`, qui prend en charge les éléments comportant 2 ou 4 composants et peut accéder à un niveau de mipmap qui est déterminé lorsque la vue est instanciée. L'échantillonnage n'est pas pris en charge.

- L'accès en lecture-écriture est fourni par la classe de modèles non spécialisée `texture_view<T, N>`, qui, comme les textures, prend en charge les éléments comportant uniquement un composant ; la vue peut accéder à un niveau de mipmap qui est déterminé lorsque la vue est instanciée. L'échantillonnage n'est pas pris en charge.

Les vues de texture sont analogues aux vues de tableaux, mais ne fournissent pas les fonctionnalités de gestion et de déplacement automatique des données qui le [array_view, classe](../../parallel/amp/reference/array-view-class.md) fournit sur le [array, classe](../../parallel/amp/reference/array-class.md). `texture_view` est accessible uniquement sur la vue d'accélérateur où les données de texture sous-jacentes résident.

### <a name="writeonlytextureview-deprecated"></a>writeonly_texture_view déconseillé

Pour Visual Studio 2013, C++ AMP introduit une meilleure prise en charge pour les fonctionnalités de texture matérielles telles que l’échantillonnage et les mipmaps, qui ne peut pas être pris en charge par le [writeonly_texture_view, classe](../../parallel/amp/reference/writeonly-texture-view-class.md). La classe `texture_view` récemment introduite, prend en charge un sur-ensemble de la fonctionnalité dans `writeonly_texture_view`; par conséquent, `writeonly_texture_view` est déconseillé.

Nous vous recommandons (au moins pour le nouveau code) d'utiliser `texture_view` pour accéder aux fonctionnalités qui ont été précédemment fournies par `writeonly_texture_view`. Comparez les deux exemples de code suivants qui accèdent en écriture à l'objet de texture comportant deux composants (int_2). Notez que dans les deux cas, la vue, `wo_tv4`, doit être capturée par la valeur de l’expression lambda. Voici l'exemple qui utilise la nouvelle classe `texture_view` :

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

Et voici la classe `writeonly_texture_view` déconseillée :

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex4(16);

    writeonly_texture_view<int_2, 1> wo_tv4(tex4);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        wo_tv4.set(idx, int_2(1, 1));
    });
}
```

Comme vous pouvez le voir, les deux exemples de code sont quasiment identiques lorsque vous vous contentez d'accéder en écriture au niveau de mipmap principal. Si vous avez utilisé `writeonly_texture_view` dans le code existant et que vous n'envisagez pas d'améliorer ce code, vous ne devez pas le modifier. Toutefois, si vous pensez présenter ce code, nous vous suggérons de le réécrire pour utiliser `texture_view` car ses améliorations prennent en charge les nouvelles fonctionnalités de texture matérielles. Lisez la suite pour plus d'informations sur ces nouvelles fonctionnalités.

Pour plus d’informations sur la désapprobation de `writeonly_texture_view`, consultez [vue d’ensemble de la conception de vue de Texture en C++ AMP](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/25/overview-of-the-texture-view-design-in-c-amp.aspx) sur la programmation parallèle en Code natif blog.

### <a name="instantiating-texture-view-objects"></a>Instanciation d'objets de la vue Texture

Déclarer un `texture_view` est similaire à la déclaration d’un `array_view` qui est associé un **tableau**. L'exemple de code suivant déclare plusieurs objets `texture` et objets `texture_view` qui leur sont associés.

```cpp
#include <amp.h>
#include <amp_graphics.h>
using namespace concurrency;
using namespace concurrency::graphics;

void declareTextureViews()
{
    // Create a 16-texel texture of int, with associated texture_views.
    texture<int, 1> intTexture(16);
    texture_view<const int, 1> intTextureViewRO(intTexture);  // read-only
    texture_view<int, 1> intTextureViewRW(intTexture);        // read-write

    // Create a 16 x 32 texture of float_2, with associated texture_views.
    texture<float_2, 2> floatTexture(16, 32);
    texture_view<const float_2, 2> floatTextureViewRO(floatTexture);  // read-only
    texture_view<float_2, 2> floatTextureViewRO(floatTexture);        // write-only

    // Create a 2 x 4 x 8 texture of uint_4, with associated texture_views.
    texture<uint_4, 3> uintTexture(2, 4, 8);
    texture_view<const uint_4, 3> uintTextureViewRO(uintTexture);  // read-only
    texture_view<uint_4, 3> uintTextureViewWO(uintTexture);        // write-only
}
```

Notez comment une vue de texture dont le type d'élément est non const avec un composant qui est en lecture-écriture, et qu'une vue de texture dont le type d'élément est non const avec plusieurs composants, sont accessibles en écriture seule. Les vues de texture des types d'élément const sont toujours en lecture seule, mais si le type d'élément est non const, le nombre de composants dans l'élément détermine s'il est accessible en lecture-écriture (1 composant) ou en écriture seule (plusieurs composants).

Le type d'élément d'une `texture_view` (son attribut const/non const et aussi le nombre de composants qu'il comporte) joue également un rôle pour déterminer si la vue prend en charge l'échantillonnage, et comment les niveaux de mipmap sont accessibles :

|Type|Composants|Lecture|Write|Échantillonnage|Accès aux mipmaps|
|----------|----------------|----------|-----------|--------------|-------------------|
|texture_view\<const T, N>|1, 2, 4|Oui|Non (1)|Oui|Oui, indexable. La plage est déterminée à l'instanciation.|
|Texture_view\<T, N >|1<br /><br /> 2, 4|Oui<br /><br /> Non (2)|Oui<br /><br /> Oui|Non (1)<br /><br /> Non (1)|Oui, un niveau. Le niveau est déterminé à l'instanciation.<br /><br /> Oui, un niveau. Le niveau est déterminé à l'instanciation.|

Dans ce tableau, vous pouvez constater que les vues de texture en lecture seule prennent en charge les nouvelles fonctions pour compenser l'impossibilité d'accéder en écriture à la vue. Les vues de texture accessibles en écriture sont limitées car elles peuvent uniquement accéder à un niveau de mipmap. Les vues de texture en lecture-écriture sont encore plus spécialisées que celles accessibles en écriture, car elles ajoutent l’exigence que le type d’élément de la vue de texture comporte uniquement un seul composant. Notez que l'exemple n'est pas pris en charge pour les vues de texture accessibles en écriture, car il s'agit d'une opération orientée lecture seule.

### <a name="reading-from-texture-view-objects"></a>Lecture des objets de la vue Texture

La lecture de données de texture non échantillonnées via un affichage de texture revient à effectuer la lecture depuis la texture elle-même, mais les textures sont capturées par référence, alors que les vues de texture sont capturées par valeur. Voici deux exemples de code. Le premier utilise uniquement `texture` :

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> text_data(16);

    parallel_for_each(extent<1>(16), [&] (index<1> idx) restrict(amp) {
        tex_data.set(idx, int_2(1, 1));
    });
}
```

Et voici le même exemple, sauf qu'il utilise maintenant la classe `texture_view` :

```cpp
void write2ComponentTexture() {
    texture<int_2, 1> tex_data(16);

    texture_view<int_2, 1> tex_view(tex_data);

    parallel_for_each(extent<1>(16), [=] (index<1> idx) restrict(amp) {
        tex_view.set(idx, int_2(1, 1));
    });
}
```

Les vues de texture dont les éléments sont basés sur les types à virgule flottante (par exemple, float, float_2 ou float_4) peuvent également être lues à l'aide de l'échantillonnage de texture afin de tirer parti de la prise en charge matérielle des différents modes de filtrage et modes d'adressage. C++ AMP prend en charge les deux modes de filtrage qui sont les plus courants dans les scénarios de calcul - le filtrage des points (voisin le plus proche) et le filtrage linéaire (moyenne pondérée) - et les quatre modes d'adressage - encapsulé, mis en miroir, ancré et associé à une bordure. Pour plus d’informations sur les modes d’adressage, consultez [address_mode, énumération](reference/concurrency-graphics-namespace-enums.md#address_mode).

Outre les modes que C++ AMP prend directement en charge, vous pouvez accéder à d'autres modes de filtrage et modes d'adressage de la plateforme sous-jacente à l'aide des API d'interopérabilité pour adopter un échantillonneur de texture créé en utilisant directement les API de plateforme. Par exemple, Direct3D prend en charge d'autres vues de filtrage, telles que le filtrage anisotropique, et peut appliquer un mode d'adressage différent à chaque dimension d'une texture. Vous pouvez créer un échantillonnage de texture dont les coordonnées sont encapsulées verticalement, mises en miroir horizontalement et échantillonnées avec le filtrage anisotropique à l'aide des API Direct3D, puis tirer parti de l'échantillonneur dans votre code C++ AMP en utilisant l'API d'interopérabilité `make_sampler`. Pour plus d’informations, consultez [échantillonnage de Texture en C++ AMP](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/07/18/texture-sampling-in-c-amp.aspx) sur la programmation parallèle en Code natif blog.

Les vues de texture prennent également en charge la lecture des mipmaps. Les vues de texture en lecture seule (celles qui ont un type d'élément const) offrent le plus de flexibilité car une plage de niveaux mip qui est déterminée à l'instanciation peut être dynamiquement échantillonnée, et parce que les éléments comportant 1, 2 ou 4 composants sont pris en charge. Les vues de texture en lecture-écriture qui ont des éléments comportant un composant prennent également en charge les mipmaps, mais uniquement d'un niveau qui est déterminé à l'instanciation. Pour plus d’informations, consultez [Texture avec Mipmaps](https://blogs.msdn.com/b/nativeconcurrency/archive/2013/08/22/texture-with-mipmaps.aspx) sur la programmation parallèle en Code natif blog.

### <a name="writing-to-texture-view-objects"></a>Écriture dans des objets de la vue Texture

Utilisez le [texture_view::Get, méthode](reference/texture-view-class.md#get) à écrire dans sous-jacent `texture` via la `texture_view` objet. Une vue de texture peut être accessible en lecture seule, en lecture-écriture ou en écriture seule. Pour qu'une vue de texture soit accessible en écriture, elle doit avoir un type d'élément non const ; pour qu'une vue de texture soit lisible et accessible en écriture, son type d'élément doit également avoir qu'un composant. Autrement, la vue de texture n'est accessible qu'en lecture seule. Vous ne pouvez accéder qu'à un niveau de mipmap d'une texture à la fois via une vue de texture, et le niveau est spécifié lorsque la vue est instanciée.

Cet exemple montre comment accéder en écriture au deuxième niveau de mipmap le plus détaillé d'une texture comportant 4 niveaux de mipmaps. Le niveau de mipmap le plus détaillé est le niveau 0.

```cpp
// Create a texture that has 4 mipmap levels : 16x16, 8x8, 4x4, 2x2
texture<int, 2> tex(extent<2>(16, 16), 16U, 4);

// Create a writable texture view to the second mipmap level :4x4
texture_view<int, 2> w_view(tex, 1);

parallel_for_each(w_view.extent, [=](index<2> idx) restrict(amp)
{
    w_view.set(idx, 123);
});
```

## <a name="interoperability"></a>Interopérabilité

Le runtime C++ AMP prend en charge l’interopérabilité entre `texture<T,1>` et [ID3D11Texture1D interface](https://go.microsoft.com/fwlink/p/?linkId=248503), entre `texture<T,2>` et [ID3D11Texture2D interface](https://go.microsoft.com/fwlink/p/?linkId=255317)et entre `texture<T,3>`et [ID3D11Texture3D interface](https://go.microsoft.com/fwlink/p/?linkId=255377). Le [get_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#get_texture) méthode prend un `texture` objet et retourne un `IUnknown` interface. Le [make_texture](reference/concurrency-graphics-direct3d-namespace-functions.md#make_texture) méthode prend un `IUnknown` interface et un `accelerator_view` objet et retourne un `texture` objet.

## <a name="see-also"></a>Voir aussi

[double_2, classe](../../parallel/amp/reference/double-2-class.md)<br/>
[double_3, classe](../../parallel/amp/reference/double-3-class.md)<br/>
[double_4, classe](../../parallel/amp/reference/double-4-class.md)<br/>
[float_2, classe](../../parallel/amp/reference/float-2-class.md)<br/>
[float_3, classe](../../parallel/amp/reference/float-3-class.md)<br/>
[float_4, classe](../../parallel/amp/reference/float-4-class.md)<br/>
[int_2, classe](../../parallel/amp/reference/int-2-class.md)<br/>
[int_3, classe](../../parallel/amp/reference/int-3-class.md)<br/>
[int_4, classe](../../parallel/amp/reference/int-4-class.md)<br/>
[norm_2, classe](../../parallel/amp/reference/norm-2-class.md)<br/>
[norm_3, classe](../../parallel/amp/reference/norm-3-class.md)<br/>
[norm_4, classe](../../parallel/amp/reference/norm-4-class.md)<br/>
[short_vector, structure](../../parallel/amp/reference/short-vector-structure.md)<br/>
[short_vector_traits, structure](../../parallel/amp/reference/short-vector-traits-structure.md)<br/>
[uint_2, classe](../../parallel/amp/reference/uint-2-class.md)<br/>
[uint_3, classe](../../parallel/amp/reference/uint-3-class.md)<br/>
[uint_4, classe](../../parallel/amp/reference/uint-4-class.md)<br/>
[unorm_2, classe](../../parallel/amp/reference/unorm-2-class.md)<br/>
[unorm_3, classe](../../parallel/amp/reference/unorm-3-class.md)<br/>
[unorm_4, classe](../../parallel/amp/reference/unorm-4-class.md)
