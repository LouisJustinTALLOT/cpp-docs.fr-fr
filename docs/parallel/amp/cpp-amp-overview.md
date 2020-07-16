---
title: Présentation de C++ AMP
ms.date: 11/19/2018
helpviewer_keywords:
- C++ Accelerated Massive Parallelism, requirements
- C++ Accelerated Massive Parallelism, architecture
- C++ AMP
- C++ Accelerated Massive Parallelism, overview
- C++ Accelerated Massive Parallelism
ms.assetid: 9e593b06-6e3c-43e9-8bae-6d89efdd39fc
ms.openlocfilehash: 5c9819c1d9167bea9a9bedeef2ac44798d5a121f
ms.sourcegitcommit: 6b3d793f0ef3bbb7eefaf9f372ba570fdfe61199
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/15/2020
ms.locfileid: "86404845"
---
# <a name="c-amp-overview"></a>Présentation de C++ AMP

C++ Accelerated Massive Parallelism (C++ AMP) accélère l’exécution du code C++ en tirant parti du matériel parallèle de données tel qu’une unité de traitement graphique (GPU) sur une carte graphique discrète. En utilisant C++ AMP, vous pouvez coder des algorithmes de données multidimensionnels afin que l’exécution puisse être accélérée en utilisant le parallélisme sur du matériel hétérogène. Le modèle de programmation C++ AMP comprend des tableaux multidimensionnels, l’indexation, le transfert mémoire, la mosaïque et une bibliothèque de fonctions mathématiques. Vous pouvez utiliser les extensions de langage C++ AMP pour contrôler la façon dont les données sont déplacées du processeur vers le GPU et inversement, afin que vous puissiez améliorer les performances.

## <a name="system-requirements"></a>Configuration système requise

- Windows 7 ou version ultérieure

- Windows Server 2008 R2 ou version ultérieure

- Matériel de niveau de fonctionnalité DirectX 11 11,0 ou version ultérieure

- Pour le débogage sur l’émulateur de logiciel, Windows 8 ou Windows Server 2012 est requis. Pour effectuer un débogage sur le matériel, vous devez installer les pilotes de votre carte graphique. Pour plus d’informations, consultez [débogage du code GPU](/visualstudio/debugger/debugging-gpu-code).

- Remarque : AMP n’est pas pris en charge actuellement sur ARM64.

## <a name="introduction"></a>Introduction

Les deux exemples suivants illustrent les principaux composants de C++ AMP. Supposons que vous souhaitez ajouter les éléments correspondants des tableaux de 2 1 dimensions. Par exemple, vous souhaiterez peut-être ajouter `{1, 2, 3, 4, 5}` et `{6, 7, 8, 9, 10}` pour obtenir `{7, 9, 11, 13, 15}` . Sans utiliser C++ AMP, vous pouvez écrire le code suivant pour ajouter les nombres et afficher les résultats.

```cpp
#include <iostream>

void StandardMethod() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5];

    for (int idx = 0; idx < 5; idx++)
    {
        sumCPP[idx] = aCPP[idx] + bCPP[idx];
    }

    for (int idx = 0; idx < 5; idx++)
    {
        std::cout << sumCPP[idx] << "\n";
    }
}
```

Les parties importantes du code sont les suivantes :

- Données : les données se composent de trois tableaux. Tous ont les mêmes rang (un) et longueur (cinq).

- Itération : la première `for` boucle fournit un mécanisme permettant d’itérer au sein des éléments des tableaux. Le code que vous souhaitez exécuter pour calculer les sommes est contenu dans le premier `for` bloc.

- Index : la `idx` variable accède aux éléments individuels des tableaux.

À l’aide de C++ AMP, vous pouvez écrire le code suivant à la place.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

const int size = 5;

void CppAmpMethod() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[size];

    // Create C++ AMP objects.
    array_view<const int, 1> a(size, aCPP);
    array_view<const int, 1> b(size, bCPP);
    array_view<int, 1> sum(size, sumCPP);
    sum.discard_data();

    parallel_for_each(
        // Define the compute domain, which is the set of threads that are created.
        sum.extent,
        // Define the code to run on each thread on the accelerator.
        [=](index<1> idx) restrict(amp) {
            sum[idx] = a[idx] + b[idx];
        }
    );

    // Print the results. The expected output is "7, 9, 11, 13, 15".
    for (int i = 0; i < size; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

Les mêmes éléments de base sont présents, mais les constructions de C++ AMP sont utilisées :

- Données : vous utilisez des tableaux C++ pour construire trois C++ AMP objets [array_view](../../parallel/amp/reference/array-view-class.md) . Vous fournissez quatre valeurs pour construire un `array_view` objet : les valeurs de données, le rang, le type d’élément et la longueur de l' `array_view` objet dans chaque dimension. Le rang et le type sont passés en tant que paramètres de type. Les données et la longueur sont passées en tant que paramètres de constructeur. Dans cet exemple, le tableau C++ passé au constructeur est unidimensionnel. Le rang et la longueur sont utilisés pour construire la forme rectangulaire des données dans l' `array_view` objet, et les valeurs de données sont utilisées pour remplir le tableau. La bibliothèque Runtime inclut également la [classe Array](../../parallel/amp/reference/array-class.md), qui a une interface qui ressemble à la `array_view` classe et est décrite plus loin dans cet article.

- Itération : la [fonction parallel_for_each (C++ amp)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) fournit un mécanisme permettant d’itérer au sein des éléments de données ou du *domaine de calcul*. Dans cet exemple, le domaine de calcul est spécifié par `sum.extent` . Le code que vous souhaitez exécuter est contenu dans une expression lambda ou une *fonction noyau*. `restrict(amp)`Indique que seul le sous-ensemble du langage C++ que C++ amp peut accélérer est utilisé.

- Index : la variable de [classe d’index](../../parallel/amp/reference/index-class.md) , `idx` , est déclarée avec un rang de 1 pour correspondre au rang de l' `array_view` objet. À l’aide de l’index, vous pouvez accéder aux éléments individuels des `array_view` objets.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Mise en forme et indexation des données : index et étendue

Vous devez définir les valeurs de données et déclarer la forme des données avant de pouvoir exécuter le code de noyau. Toutes les données sont définies comme un tableau (rectangulaire) et vous pouvez définir le tableau pour qu’il ait un rang (nombre de dimensions). Les données peuvent avoir n’importe quelle taille dans toutes les dimensions.

### <a name="index-class"></a>index, classe

La [classe index](../../parallel/amp/reference/index-class.md) spécifie un emplacement dans `array` l' `array_view` objet ou en encapsulant l’offset de l’origine dans chaque dimension dans un objet. Lorsque vous accédez à un emplacement dans le tableau, vous transmettez un `index` objet à l’opérateur d’indexation, `[]` , au lieu d’une liste d’index entiers. Vous pouvez accéder aux éléments de chaque dimension à l’aide de l’opérateur [Array :: Operator ()](reference/array-class.md#operator_call) ou [array_view :: Operator ()](reference/array-view-class.md#operator_call).

L’exemple suivant crée un index unidimensionnel qui spécifie le troisième élément dans un objet unidimensionnel `array_view` . L’index est utilisé pour imprimer le troisième élément de l' `array_view` objet. La sortie est 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

L’exemple suivant crée un index à deux dimensions qui spécifie l’élément où la ligne = 1 et la colonne = 2 dans un objet à deux dimensions `array_view` . Le premier paramètre dans le `index` constructeur est le composant de ligne, et le deuxième paramètre est le composant de colonne. La sortie est 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

L’exemple suivant crée un index à trois dimensions qui spécifie l’élément dont la profondeur est égale à 0, la ligne = 1 et la colonne = 3 dans un objet en trois dimensions `array_view` . Notez que le premier paramètre est le composant de profondeur, le deuxième paramètre est le composant de ligne, et le troisième paramètre est le composant de colonne. La sortie est 8.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};

array_view<int, 3> a(2, 3, 4, aCPP);

// Specifies the element at 3, 1, 0.
index<3> idx(0, 1, 3);

std::cout << a[idx] << "\n";
// Output: 8
```

### <a name="extent-class"></a>extent, classe

La [classe extent](../../parallel/amp/reference/extent-class.md) spécifie la longueur des données dans chaque dimension de `array` l' `array_view` objet ou. Vous pouvez créer une étendue et l’utiliser pour créer un `array` `array_view` objet ou. Vous pouvez également récupérer l’étendue d’un `array` objet ou existant `array_view` . L’exemple suivant imprime la longueur de l’étendue dans chaque dimension d’un `array_view` objet.

```cpp
int aCPP[] = {
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12,
    1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12};
// There are 3 rows and 4 columns, and the depth is two.
array_view<int, 3> a(2, 3, 4, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
std::cout << "Length in most significant dimension is " << a.extent[0] << "\n";
```

L’exemple suivant crée un `array_view` objet qui a les mêmes dimensions que l’objet dans l’exemple précédent, mais cet exemple utilise un `extent` objet au lieu d’utiliser des paramètres explicites dans le `array_view` constructeur.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24};
extent<3> e(2, 3, 4);

array_view<int, 3> a(e, aCPP);

std::cout << "The number of columns is " << a.extent[2] << "\n";
std::cout << "The number of rows is " << a.extent[1] << "\n";
std::cout << "The depth is " << a.extent[0] << "\n";
```

## <a name="moving-data-to-the-accelerator-array-and-array_view"></a>Déplacement de données vers l’accélérateur : Array et array_view

Deux conteneurs de données utilisés pour déplacer des données vers l’accélérateur sont définis dans la bibliothèque Runtime. Il s’agit de la [classe Array](../../parallel/amp/reference/array-class.md) et de la [classe array_view](../../parallel/amp/reference/array-view-class.md). La `array` classe est une classe de conteneur qui crée une copie complète des données lorsque l’objet est construit. La `array_view` classe est une classe wrapper qui copie les données lorsque la fonction noyau accède aux données. Lorsque les données sont nécessaires sur l’appareil source, les données sont recopiées.

### <a name="array-class"></a>array, classe

Lorsqu’un `array` objet est construit, une copie complète des données est créée sur l’accélérateur si vous utilisez un constructeur qui comprend un pointeur vers le jeu de données. La fonction de noyau modifie la copie sur l’accélérateur. Lorsque l’exécution de la fonction de noyau est terminée, vous devez copier les données dans la structure de données source. L’exemple suivant multiplie chaque élément dans un vecteur par 10. Une fois la fonction de noyau terminée, le `vector conversion operator` est utilisé pour recopier les données dans l’objet Vector.

```cpp
std::vector<int> data(5);

for (int count = 0; count <5; count++)
{
    data[count] = count;
}

array<int, 1> a(5, data.begin(), data.end());

parallel_for_each(
    a.extent,
    [=, &a](index<1> idx) restrict(amp) {
        a[idx] = a[idx]* 10;
    });

data = a;
for (int i = 0; i < 5; i++)
{
    std::cout << data[i] << "\n";
}
```

### <a name="array_view-class"></a>array_view, classe

Le `array_view` a presque les mêmes membres que la `array` classe, mais le comportement sous-jacent n’est pas le même. Les données passées au `array_view` constructeur ne sont pas répliquées sur le GPU comme c’est le cas avec un `array` constructeur. Au lieu de cela, les données sont copiées vers l’accélérateur lorsque la fonction noyau est exécutée. Par conséquent, si vous créez deux `array_view` objets qui utilisent les mêmes données, les deux `array_view` objets font référence au même espace mémoire. Dans ce cas, vous devez synchroniser tout accès multithread. Le principal avantage de l’utilisation de la `array_view` classe est que les données sont déplacées uniquement si elles sont nécessaires.

### <a name="comparison-of-array-and-array_view"></a>Comparaison entre tableau et array_view

Le tableau suivant récapitule les similitudes et les différences entre les `array` `array_view` classes et.

|Description|array (classe)|array_view (classe)|
|-----------------|-----------------|-----------------------|
|Quand le rang est déterminé|Au moment de la compilation.|Au moment de la compilation.|
|Lorsque l’étendue est déterminée|Au moment de l’exécution.|Au moment de l’exécution.|
|Graphique à base de formes|Rectangulaire.|Rectangulaire.|
|Stockage des données|Est un conteneur de données.|Est un wrapper de données.|
|Copier|Copie complète et explicite au niveau de la définition.|Copie implicite lorsque la fonction noyau y accède.|
|Récupération de données|En recopiant les données du tableau dans un objet sur le thread de l’UC.|En accédant directement à l' `array_view` objet ou en appelant la [méthode array_view :: Synchronize](reference/array-view-class.md#synchronize) pour continuer à accéder aux données sur le conteneur d’origine.|

### <a name="shared-memory-with-array-and-array_view"></a>Mémoire partagée avec tableau et array_view

La mémoire partagée est une mémoire accessible à la fois par l’UC et l’accélérateur. L’utilisation de la mémoire partagée permet d’éliminer ou de réduire considérablement la surcharge liée à la copie de données entre l’UC et l’accélérateur. Bien que la mémoire soit partagée, elle ne peut pas être accessible simultanément à la fois par l’UC et l’accélérateur, ce qui entraîne un comportement indéfini.

`array`les objets peuvent être utilisés pour spécifier un contrôle affiné de l’utilisation de la mémoire partagée si l’accélérateur associé le prend en charge. Le fait qu’un accélérateur prenne en charge la mémoire partagée est déterminé par la propriété [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) de l’accélérateur, qui renvoie la **valeur true** lorsque la mémoire partagée est prise en charge. Si la mémoire partagée est prise en charge, l' [énumération access_type](reference/concurrency-namespace-enums-amp.md#access_type) par défaut pour les allocations de mémoire sur l’accélérateur est déterminée par la `default_cpu_access_type` propriété. Par défaut, `array` les `array_view` objets et prennent la même valeur `access_type` que le principal associé `accelerator` .

En définissant la propriété de [membre de données Array :: cpu_access_type](reference/array-class.md#cpu_access_type) d’un `array` explicitement, vous pouvez exercer un contrôle affiné sur la façon dont la mémoire partagée est utilisée, afin que vous puissiez optimiser l’application pour les caractéristiques de performances du matériel, en fonction des modèles d’accès mémoire de ses noyaux de calcul. Un `array_view` reflète le même que celui `cpu_access_type` `array` auquel il est associé ; ou, si le array_view est construit sans source de données, son `access_type` reflète l’environnement qui l’amène d’abord à allouer du stockage. Autrement dit, s’il est accédé pour la première fois par l’hôte (UC), il se comporte comme s’il avait été créé sur une source de données de processeur et partage le `access_type` du `accelerator_view` associé par capture ; Toutefois, s’il est d’abord accessible par un `accelerator_view` , il se comporte comme s’il avait été créé `array` sur un créé sur ce `accelerator_view` et partage le `array` `access_type` .

L’exemple de code suivant montre comment déterminer si l’accélérateur par défaut prend en charge la mémoire partagée, puis crée plusieurs tableaux avec différentes configurations de cpu_access_type.

```cpp
#include <amp.h>
#include <iostream>

using namespace Concurrency;

int main()
{
    accelerator acc = accelerator(accelerator::default_accelerator);

    // Early out if the default accelerator doesn’t support shared memory.
    if (!acc.supports_cpu_shared_memory)
    {
        std::cout << "The default accelerator does not support shared memory" << std::endl;
        return 1;
    }

    // Override the default CPU access type.
    acc.default_cpu_access_type = access_type_read_write

    // Create an accelerator_view from the default accelerator. The
    // accelerator_view inherits its default_cpu_access_type from acc.
    accelerator_view acc_v = acc.default_view;

    // Create an extent object to size the arrays.
    extent<1> ex(10);

    // Input array that can be written on the CPU.
    array<int, 1> arr_w(ex, acc_v, access_type_write);

    // Output array that can be read on the CPU.
    array<int, 1> arr_r(ex, acc_v, access_type_read);

    // Read-write array that can be both written to and read from on the CPU.
    array<int, 1> arr_rw(ex, acc_v, access_type_read_write);
}
```

## <a name="executing-code-over-data-parallel_for_each"></a>Exécution de code sur les données : parallel_for_each

La fonction [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) définit le code que vous souhaitez exécuter sur l’accélérateur par rapport aux données de l' `array` `array_view` objet ou. Prenons le code suivant de l’introduction de cette rubrique.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddArrays() {
    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp)
        {
            sum[idx] = a[idx] + b[idx];
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

La `parallel_for_each` méthode accepte deux arguments, un domaine de calcul et une expression lambda.

Le *domaine de calcul* est un `extent` objet ou un `tiled_extent` objet qui définit l’ensemble de threads à créer pour une exécution en parallèle. Un thread est généré pour chaque élément dans le domaine de calcul. Dans ce cas, l' `extent` objet est unidimensionnel et comporte cinq éléments. Par conséquent, cinq threads sont démarrés.

L' *expression lambda* définit le code à exécuter sur chaque thread. La clause de capture, `[=]` , spécifie que le corps de l’expression lambda accède à toutes les variables capturées par valeur, qui sont, dans ce cas `a` ,, `b` et `sum` . Dans cet exemple, la liste de paramètres crée une variable unidimensionnelle `index` nommée `idx` . La valeur de `idx[0]` est 0 dans le premier thread et augmente d’une unité dans chaque thread suivant. `restrict(amp)`Indique que seul le sous-ensemble du langage C++ que C++ amp peut accélérer est utilisé.  Les limitations relatives aux fonctions qui ont le modificateur Restrict sont décrites dans [restreindre (C++ amp)](../../cpp/restrict-cpp-amp.md). Pour plus d’informations, consultez [syntaxe de l’expression lambda](../../cpp/lambda-expression-syntax.md).

L’expression lambda peut inclure le code à exécuter ou elle peut appeler une fonction de noyau distincte. La fonction de noyau doit inclure le `restrict(amp)` modificateur. L’exemple suivant est équivalent à l’exemple précédent, mais il appelle une fonction de noyau distincte.

```cpp
#include <amp.h>
#include <iostream>
using namespace concurrency;

void AddElements(
    index<1> idx,
    array_view<int, 1> sum,
    array_view<int, 1> a,
    array_view<int, 1> b) restrict(amp) {
    sum[idx] = a[idx] + b[idx];
}

void AddArraysWithFunction() {

    int aCPP[] = {1, 2, 3, 4, 5};
    int bCPP[] = {6, 7, 8, 9, 10};
    int sumCPP[5] = {0, 0, 0, 0, 0};

    array_view<int, 1> a(5, aCPP);
    array_view<int, 1> b(5, bCPP);
    array_view<int, 1> sum(5, sumCPP);

    parallel_for_each(
        sum.extent,
        [=](index<1> idx) restrict(amp) {
            AddElements(idx, sum, a, b);
        }
    );

    for (int i = 0; i < 5; i++) {
        std::cout << sum[i] << "\n";
    }
}
```

## <a name="accelerating-code-tiles-and-barriers"></a>Accélération du code : vignettes et barrières

Vous pouvez obtenir une accélération supplémentaire à l’aide de la mosaïque. La mosaïque divise les threads en sous-ensembles rectangulaires égaux ou en *mosaïques*. Vous déterminez la taille de mosaïque appropriée en fonction de votre jeu de données et de l’algorithme que vous codez. Pour chaque thread, vous avez accès à l’emplacement *Global* d’un élément de données par rapport à l’ensemble `array` ou `array_view` à l’accès à l’emplacement *local* relatif à la vignette. L’utilisation de la valeur d’index locale simplifie votre code, car vous n’avez pas besoin d’écrire le code pour convertir les valeurs d’index de global à local. Pour utiliser la mosaïque, appelez la [méthode extent :: Tile](reference/extent-class.md#tile) sur le domaine de calcul dans la `parallel_for_each` méthode et utilisez un objet [tiled_index](../../parallel/amp/reference/tiled-index-class.md) dans l’expression lambda.

Dans les applications classiques, les éléments d’une vignette sont liés d’une manière ou d’une autre, et le code doit accéder à et effectuer le suivi des valeurs sur la vignette. Pour ce faire, utilisez le mot clé [Tile_static mot](../../cpp/tile-static-keyword.md) clé et la [méthode tile_barrier :: wait](reference/tile-barrier-class.md#wait) . Une variable qui a le mot clé **tile_static** a une portée sur toute une vignette, et une instance de la variable est créée pour chaque vignette. Vous devez gérer la synchronisation de l’accès aux threads de mosaïques à la variable. La [méthode tile_barrier :: wait](reference/tile-barrier-class.md#wait) arrête l’exécution du thread actuel jusqu’à ce que tous les threads de la mosaïque aient atteint l’appel à `tile_barrier::wait` . Vous pouvez ainsi accumuler des valeurs sur la vignette à l’aide de variables de **tile_static** . Vous pouvez ensuite terminer les calculs qui requièrent l’accès à toutes les valeurs.

Le diagramme suivant représente un tableau à deux dimensions de données d’échantillonnage qui est organisé en mosaïques.

![Valeurs d'index dans une étendue en mosaïque](../../parallel/amp/media/camptiledgridexample.png "Valeurs d'index dans une étendue en mosaïque")

L’exemple de code suivant utilise les données d’échantillonnage du diagramme précédent. Le code remplace chaque valeur de la vignette par la moyenne des valeurs dans la vignette.

```cpp
// Sample data:
int sampledata[] = {
    2, 2, 9, 7, 1, 4,
    4, 4, 8, 8, 3, 4,
    1, 5, 1, 2, 5, 2,
    6, 8, 3, 2, 7, 2};

// The tiles:
// 2 2    9 7    1 4
// 4 4    8 8    3 4
//
// 1 5    1 2    5 2
// 6 8    3 2    7 2

// Averages:
int averagedata[] = {
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
    0, 0, 0, 0, 0, 0,
};

array_view<int, 2> sample(4, 6, sampledata);

array_view<int, 2> average(4, 6, averagedata);

parallel_for_each(
    // Create threads for sample.extent and divide the extent into 2 x 2 tiles.
    sample.extent.tile<2,2>(),
        [=](tiled_index<2,2> idx) restrict(amp) {
        // Create a 2 x 2 array to hold the values in this tile.
        tile_static int nums[2][2];

        // Copy the values for the tile into the 2 x 2 array.
        nums[idx.local[1]][idx.local[0]] = sample[idx.global];

        // When all the threads have executed and the 2 x 2 array is complete, find the average.
        idx.barrier.wait();
        int sum = nums[0][0] + nums[0][1] + nums[1][0] + nums[1][1];

        // Copy the average into the array_view.
        average[idx.global] = sum / 4;
    });

for (int i = 0; i <4; i++) {
    for (int j = 0; j <6; j++) {
        std::cout << average(i,j) << " ";
    }
    std::cout << "\n";
}

// Output:
// 3 3 8 8 3 3
// 3 3 8 8 3 3
// 5 5 2 2 4 4
// 5 5 2 2 4 4
```

## <a name="math-libraries"></a>Bibliothèques mathématiques

C++ AMP comprend deux bibliothèques mathématiques. La bibliothèque à double précision dans l' [espace de noms Concurrency ::p recise_math](../../parallel/amp/reference/concurrency-precise-math-namespace.md) fournit la prise en charge des fonctions à double précision. Il fournit également la prise en charge des fonctions à simple précision, bien que la prise en charge de la double précision sur le matériel soit toujours nécessaire. Elle est conforme à la [spécification C99 (ISO/IEC 9899)](https://go.microsoft.com/fwlink/p/?linkid=225887). L’accélérateur doit prendre en charge la double précision complète. Vous pouvez déterminer si c’est le cas en vérifiant la valeur du [membre de données Accelerator :: supports_double_precision](reference/accelerator-class.md#supports_double_precision). La bibliothèque Math rapide, dans l' [espace de noms Concurrency :: fast_math](../../parallel/amp/reference/concurrency-fast-math-namespace.md), contient un autre jeu de fonctions mathématiques. Ces fonctions, qui prennent en charge uniquement les `float` opérandes, s’exécutent plus rapidement, mais ne sont pas aussi précises que celles de la bibliothèque mathématique double précision. Les fonctions sont contenues dans le \<amp_math.h> fichier d’en-tête et toutes sont déclarées avec `restrict(amp)` . Les fonctions du \<cmath> fichier d’en-tête sont importées dans les `fast_math` espaces de noms et `precise_math` . Le mot clé **restrict** est utilisé pour distinguer la version \<cmath> et la version de C++ amp. Le code suivant calcule le logarithme en base 10, à l’aide de la méthode Fast, de chaque valeur figurant dans le domaine de calcul.

```cpp
#include <amp.h>
#include <amp_math.h>
#include <iostream>
using namespace concurrency;

void MathExample() {

    double numbers[] = { 1.0, 10.0, 60.0, 100.0, 600.0, 1000.0 };
    array_view<double, 1> logs(6, numbers);

    parallel_for_each(
        logs.extent,
        [=] (index<1> idx) restrict(amp) {
            logs[idx] = concurrency::fast_math::log10(numbers[idx]);
        }
    );

    for (int i = 0; i < 6; i++) {
        std::cout << logs[i] << "\n";
    }
}
```

## <a name="graphics-library"></a>Bibliothèque de graphiques

C++ AMP comprend une bibliothèque de graphiques conçue pour la programmation graphique accélérée. Cette bibliothèque est utilisée uniquement sur les appareils qui prennent en charge les fonctionnalités graphiques natives. Les méthodes se trouvent dans l' [espace de noms Concurrency :: Graphics](../../parallel/amp/reference/concurrency-graphics-namespace.md) et sont contenues dans le \<amp_graphics.h> fichier d’en-tête. Les composants clés de la bibliothèque Graphics sont les suivants :

- [classe texture](../../parallel/amp/reference/texture-class.md): vous pouvez utiliser la classe texture pour créer des textures à partir de la mémoire ou à partir d’un fichier. Les textures ressemblent à des tableaux parce qu’elles contiennent des données et qu’elles ressemblent à des conteneurs dans la bibliothèque standard C++ en ce qui concerne la construction d’assignation et de copie. Pour plus d’informations, consultez [Conteneurs disponibles dans la bibliothèque standard C++](../../standard-library/stl-containers.md). Les paramètres de modèle pour la `texture` classe sont le type d’élément et le rang. Le rang peut être 1, 2 ou 3. Le type d’élément peut être l’un des types de vecteurs courts décrits plus loin dans cet article.

- [classe writeonly_texture_view](../../parallel/amp/reference/writeonly-texture-view-class.md): fournit un accès en écriture seule à n’importe quelle texture.

- Short Vector Library : définit un ensemble de types de vecteurs courts de longueur 2, 3 et 4 basés sur **int**, `uint` , **float**, **double**, [normal](../../parallel/amp/reference/norm-class.md)ou [unorm](../../parallel/amp/reference/unorm-class.md).

## <a name="universal-windows-platform-uwp-apps"></a>Applications de la plateforme Windows universelle (UWP)

À l’instar des autres bibliothèques C++, vous pouvez utiliser C++ AMP dans vos applications UWP. Ces articles décrivent comment inclure C++ AMP code dans les applications créées à l’aide de C++, C#, Visual Basic ou JavaScript :

- [Utilisation de C++ AMP dans des applications UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Procédure pas à pas : création d’un composant de Windows Runtime de base en C++ et appel de ce dernier à partir de JavaScript](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [Optimiseur de voyage Bing Maps, application Windows Store en JavaScript et C++](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [Comment utiliser C++ AMP à partir de C# à l’aide de l’Windows Runtime](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c-using-winrt/)

- [Comment utiliser C++ AMP à partir de C #](https://devblogs.microsoft.com/pfxteam/how-to-use-c-amp-from-c/)

- [Appel de fonctions natives à partir de code managé](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP et visualiseur concurrentiel

Le visualiseur concurrentiel prend en charge l’analyse des performances de C++ AMP code. Ces articles décrivent ces fonctionnalités :

- [Graphique d'activité GPU](/visualstudio/profiling/gpu-activity-graph)

- [Activité GPU (pagination)](/visualstudio/profiling/gpu-activity-paging)

- [Activité GPU (ce processus)](/visualstudio/profiling/gpu-activity-this-process)

- [Activité GPU (autres processus)](/visualstudio/profiling/gpu-activity-other-processes)

- [Canaux (vue Threads)](/visualstudio/profiling/channels-threads-view)

- [Analyse du code C++ AMP avec le visualiseur concurrentiel](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)

## <a name="performance-recommendations"></a>Recommandations sur les performances

Le modulo et la Division des entiers non signés offrent de meilleures performances que le modulo et la Division des entiers signés. Nous vous recommandons d’utiliser des entiers non signés lorsque cela est possible.

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Référence (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Blog sur la programmation parallèle en code natif](https://go.microsoft.com/fwlink/p/?linkid=238472)
