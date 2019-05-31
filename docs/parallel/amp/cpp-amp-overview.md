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
ms.openlocfilehash: 4098a1467b0f81b5f66a2e45a4bb2138e8c1c262
ms.sourcegitcommit: 28eae422049ac3381c6b1206664455dbb56cbfb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/31/2019
ms.locfileid: "66449949"
---
# <a name="c-amp-overview"></a>Présentation de C++ AMP

C++ Accelerated Massive (C++ AMP Parallelism) accélère l’exécution du code C++ en tirant parti du matériel parallèle de données comme une unité de traitement graphique (GPU) sur une carte graphique discrète. À l’aide de C++ AMP, vous pouvez coder les algorithmes multidimensionnels de données afin que l’exécution peut être accélérée à l’aide de parallélisme sur du matériel hétérogène. Le modèle de programmation C++ AMP comprend des tableaux multidimensionnels, l’indexation, le transfert mémoire, la mosaïque et une bibliothèque de fonctions mathématiques. Vous pouvez utiliser des extensions de langage C++ AMP pour contrôler comment les données sont déplacées de l’unité centrale vers le GPU et inversement, afin que vous pouvez améliorer les performances.

## <a name="system-requirements"></a>Configuration système requise

- Windows 7 ou version ultérieure

- Windows Server 2008 R2 ou une version ultérieure

- DirectX 11 fonctionnalité niveau 11.0 ou matériel plus récent

- Pour le débogage sur l’émulateur de logiciel, Windows 8 ou Windows Server 2012 est nécessaire. Pour effectuer un débogage sur le matériel, vous devez installer les pilotes de votre carte graphique. Pour plus d’informations, consultez [débogage du Code GPU](/visualstudio/debugger/debugging-gpu-code).

- Remarque : AMP n’est actuellement pas pris en charge sur ARM64.

## <a name="introduction"></a>Introduction

Les deux exemples suivants illustrent les composants principaux de C++ AMP. Supposons que vous voulez ajouter les éléments correspondants de deux tableaux unidimensionnels. Par exemple, vous souhaiterez peut-être ajouter `{1, 2, 3, 4, 5}` et `{6, 7, 8, 9, 10}` obtenir `{7, 9, 11, 13, 15}`. Sans utiliser C++ AMP, vous pouvez écrire le code suivant pour ajouter les nombres et afficher les résultats.

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

- Données : Les données se composent de trois tableaux. Tous ont les mêmes rang (un) et longueur (cinq).

- Itération : Le premier `for` boucle fournit un mécanisme pour itérer les éléments dans les tableaux. Le code que vous souhaitez exécuter pour calculer les sommes est contenu dans la première `for` bloc.

- Index : Le `idx` variable accède aux éléments des tableaux.

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

Les mêmes éléments de base sont présents, mais les constructions C++ AMP sont utilisées :

- Données : Vous utilisez C++ tableaux pour construire trois C++ AMP [array_view](../../parallel/amp/reference/array-view-class.md) objets. Vous fournissez quatre valeurs pour construire un `array_view` objet : les valeurs de données, le rang, le type d’élément et la longueur de la `array_view` objet dans chaque dimension. Le rang et le type sont passés en tant que paramètres de type. Les données et la longueur sont passées comme paramètres du constructeur. Dans cet exemple, le tableau C++ qui est passé au constructeur est unidimensionnel. Le rang et la longueur sont utilisés pour construire la forme rectangulaire des données dans le `array_view` objet et les valeurs sont utilisées pour remplir le tableau de données. La bibliothèque runtime inclut également le [array, classe](../../parallel/amp/reference/array-class.md), qui possède une interface qui ressemble à la `array_view` classe et est décrit plus loin dans cet article.

- Itération : Le [parallel_for_each, fonction (C++ AMP)](reference/concurrency-namespace-functions-amp.md#parallel_for_each) fournit un mécanisme pour itérer les éléments de données, ou *domaine de calcul*. Dans cet exemple, le domaine de calcul spécifié par `sum.extent`. Le code que vous souhaitez exécuter est contenu dans une expression lambda, ou *fonction noyau*. La `restrict(amp)` indique que seul le sous-ensemble du langage C++ que C++ AMP peut accélérer est utilisé.

- Index : Le [index, classe](../../parallel/amp/reference/index-class.md) variable, `idx`, est déclaré avec un rang d’un pour correspondre au rang de le `array_view` objet. À l’aide de l’index, vous pouvez accédez aux éléments individuels de la `array_view` objets.

## <a name="shaping-and-indexing-data-index-and-extent"></a>Mise en forme et indexation des données : index et extent

Vous devez définir les valeurs de données et déclarer la forme des données avant de pouvoir exécuter le code du noyau. Toutes les données est défini comme étant un tableau rectangulaire, et vous pouvez définir le tableau pour n’importe quel rang (nombre de dimensions). Les données peuvent être n’importe quelle taille dans les dimensions.

### <a name="index-class"></a>index, classe

Le [index, classe](../../parallel/amp/reference/index-class.md) spécifie un emplacement dans le `array` ou `array_view` objet en encapsulant le décalage à partir de l’origine dans chaque dimension dans un seul objet. Lorsque vous accédez à un emplacement dans le tableau, vous passez un `index` objet à l’opérateur d’indexation, `[]`, au lieu d’une liste d’index d’entiers. Vous pouvez accéder aux éléments dans chaque dimension à l’aide de la [Array::operator opérateur](reference/array-class.md#operator_call) ou [array_view::operator() opérateur](reference/array-view-class.md#operator_call).

L’exemple suivant crée un index unidimensionnel qui spécifie le troisième élément dans une dimension `array_view` objet. L’index est utilisé pour imprimer le troisième élément dans le `array_view` objet. Le résultat est 3.

```cpp
int aCPP[] = {1, 2, 3, 4, 5};
array_view<int, 1> a(5, aCPP);

index<1> idx(2);

std::cout << a[idx] << "\n";
// Output: 3
```

L’exemple suivant crée un index à deux dimensions qui spécifie l’élément où la ligne = 1 et la colonne = 2 un à deux dimensions `array_view` objet. Le premier paramètre dans le `index` constructeur est le composant de ligne, et le deuxième paramètre est le composant de colonne. La sortie est 6.

```cpp
int aCPP[] = {1, 2, 3, 4, 5, 6};
array_view<int, 2> a(2, 3, aCPP);

index<2> idx(1, 2);

std::cout <<a[idx] << "\n";
// Output: 6
```

L’exemple suivant crée un index en trois dimensions qui spécifie l’élément où la profondeur = 0, la ligne = 1 et la colonne = 3 un à trois dimensions `array_view` objet. Notez que le premier paramètre est le composant de profondeur, le deuxième paramètre est le composant de ligne, et le troisième paramètre est le composant de colonne. La sortie est 8.

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

Le [extent, classe](../../parallel/amp/reference/extent-class.md) spécifie la longueur des données dans chaque dimension de la `array` ou `array_view` objet. Vous pouvez créer une étendue et l’utiliser pour créer un `array` ou `array_view` objet. Vous pouvez également récupérer l’étendue d’un existant `array` ou `array_view` objet. L’exemple suivant imprime la longueur de l’étendue dans chaque dimension d’un `array_view` objet.

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

## <a name="moving-data-to-the-accelerator-array-and-arrayview"></a>Déplacement des données à l’accélérateur : array et array_view

Deux conteneurs de données utilisés pour déplacer des données à l’accélérateur sont définis dans la bibliothèque runtime. Ils sont le [array, classe](../../parallel/amp/reference/array-class.md) et [array_view, classe](../../parallel/amp/reference/array-view-class.md). Le `array` est une classe de conteneur qui crée une copie complète des données lorsque l’objet est construit. Le `array_view` classe est une classe wrapper qui copie les données lorsque la fonction noyau accède aux données. Lorsque les données sont requises sur l’appareil source les données sont copiées en retour.

### <a name="array-class"></a>array, classe

Quand un `array` objet est construit, une copie complète des données est créée sur l’accélérateur si vous utilisez un constructeur qui inclut un pointeur vers le jeu de données. La fonction noyau modifie la copie sur l’accélérateur. Lorsque l’exécution de la fonction noyau est terminée, vous devez copier les données dans l’arborescence de données source. L’exemple suivant multiplie chaque élément d’un vecteur par 10. Une fois la fonction noyau est terminée, le `vector conversion operator` est utilisé pour copier les données dans l’objet vector.

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

### <a name="arrayview-class"></a>array_view, classe

Le `array_view` a presque les mêmes membres que la `array` classe, mais le comportement sous-jacent n’est pas le même. Données passées à la `array_view` constructeur n’est pas répliqué sur le GPU, comme c’est avec un `array` constructeur. Au lieu de cela, les données sont copiées à l’accélérateur lorsque la fonction noyau est exécutée. Par conséquent, si vous créez deux `array_view` les objets qui utilisent les mêmes données, les deux `array_view` objets font référence au même espace de mémoire. Lorsque vous effectuez cette opération, vous devez synchroniser tout accès multithread. Le principal avantage de l’utilisation de la `array_view` classe est que les données sont déplacées uniquement s’il est nécessaire.

### <a name="comparison-of-array-and-arrayview"></a>Comparaison d’array et array_view

Le tableau suivant résume les similitudes et les différences entre le `array` et `array_view` classes.

|Description|array (classe)|array_view (classe)|
|-----------------|-----------------|-----------------------|
|Lorsque le rang est déterminé|Au moment de la compilation.|Au moment de la compilation.|
|Lorsque l’étendue est déterminée|Au moment de l’exécution.|Au moment de l’exécution.|
|Forme|Rectangulaire.|Rectangulaire.|
|Stockage de données|Est un conteneur de données.|Est un wrapper de données.|
|Copier|Copie complète et explicite au niveau de définition.|Copie implicite lorsqu’il est accessible par la fonction noyau.|
|Récupération de données|En copiant les données de tableau dans un objet sur le thread de processeur.|Par accès direct de la `array_view` de l’objet ou en appelant le [array_view::Synchronize, méthode](reference/array-view-class.md#synchronize) continuer à accéder à des données sur le conteneur d’origine.|

### <a name="shared-memory-with-array-and-arrayview"></a>Mémoire partagée avec array et array_view

Mémoire partagée est la mémoire qui est accessible par le processeur et de l’accélérateur. L’utilisation de la mémoire partagée élimine ou réduit considérablement la surcharge de copie des données entre l’UC et de l’accélérateur. Bien que la mémoire est partagée, il ne peut pas être accessibles simultanément par le processeur et de l’accélérateur, et cela entraîne un comportement non défini.

`array` objets peuvent être utilisés pour spécifier un contrôle affiné sur l’utilisation de la mémoire partagée si l’accélérateur associé la prend en charge. Si un accélérateur prend en charge la mémoire partagée est déterminé par l’accélérateur [supports_cpu_shared_memory](reference/accelerator-class.md#supports_cpu_shared_memory) propriété, qui retourne **true** quand la prise en charge de mémoire partagée. Si la mémoire partagée est prise en charge, la valeur par défaut [access_type, énumération](reference/concurrency-namespace-enums-amp.md#access_type) pour mémoire allocations sur l’accélérateur est déterminé par le `default_cpu_access_type` propriété. Par défaut, `array` et `array_view` objets prennent le même `access_type` que le principal associé `accelerator`.

En définissant le [array::cpu_access_type, membre de données](reference/array-class.md#cpu_access_type) propriété d’un `array` explicitement, vous pouvez contrôler avec précision la mémoire partagée comment est utilisée, afin que vous pouvez optimiser l’application pour des performances de matériel caractéristiques, en fonction des modèles d’accès mémoire de ses cœurs de calcul. Un `array_view` reflète le même `cpu_access_type` en tant que le `array` qui lui est associée ; ou, si l’array_view est construit sans source de données, son `access_type` reflète l’environnement qui a entraîné à allouer du stockage. Autrement dit, si elle est tout d’abord accessible par l’hôte (UC), puis il se comporte comme s’il a été créé sur une source de données du processeur et les partages le `access_type` de la `accelerator_view` associé par capture ; Toutefois, si elle est d’abord accessible par un `accelerator_view`, il se comporte comme s’il s’agissait créé via un `array` créées sur cet `accelerator_view` et partage le `array`de `access_type`.

L’exemple de code suivant montre comment déterminer si l’accélérateur par défaut prend en charge de la mémoire partagée, puis crée plusieurs tableaux dont les configurations cpu_access_type sont différentes.

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

## <a name="executing-code-over-data-parallelforeach"></a>L’exécution de Code sur les données : parallel_for_each

Le [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) fonction définit le code que vous souhaitez exécuter sur l’accélérateur sur les données dans le `array` ou `array_view` objet. Prenons le code suivant à partir de l’introduction de cette rubrique.

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

Le `parallel_for_each` méthode accepte deux arguments, un domaine de calcul et une expression lambda.

Le *domaine de calcul* est un `extent` objet ou un `tiled_extent` objet qui définit l’ensemble des threads à créer pour l’exécution parallèle. Un thread est généré pour chaque élément dans le domaine de calcul. Dans ce cas, le `extent` objet est unidimensionnel et comporte cinq éléments. Par conséquent, cinq threads sont démarrés.

Le *expression lambda* définit le code à exécuter sur chaque thread. La clause de capture, `[=]`, spécifie que le corps de l’expression lambda accède à toutes les variables capturées par valeur, qui sont dans ce cas `a`, `b`, et `sum`. Dans cet exemple, la liste de paramètres crée une dimension `index` variable nommée `idx`. La valeur de la `idx[0]` est 0 dans le premier thread et augmente d’une unité dans chaque thread suivant. La `restrict(amp)` indique que seul le sous-ensemble du langage C++ que C++ AMP peut accélérer est utilisé.  Les limitations sur les fonctions qui ont le modificateur de restriction sont décrites dans [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md). Pour plus d’informations, consultez, [syntaxe d’Expression Lambda](../../cpp/lambda-expression-syntax.md).

L’expression lambda peut inclure le code à exécuter, ou elle peut appeler une fonction noyau distincte. La fonction noyau doit inclure le `restrict(amp)` modificateur. L’exemple suivant est équivalent à l’exemple précédent, mais il appelle une fonction noyau distincte.

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

## <a name="accelerating-code-tiles-and-barriers"></a>Accélérer le Code : Mosaïques et cloisonnements

Vous pouvez obtenir l’accélération supplémentaire à l’aide de la mosaïque. Mosaïque divise les threads en sous-ensembles rectangulaires égaux ou *vignettes*. Vous déterminez la taille de la vignette appropriée en fonction de votre jeu de données et de l’algorithme que vous codez. Pour chaque thread, vous avez accès à la *global* emplacement d’un élément de données par rapport à la totalité `array` ou `array_view` et l’accès à la *local* emplacement relatif à la vignette. À l’aide de la valeur d’index local simplifie le code, car vous n’êtes pas obligé d’écrire le code pour convertir des valeurs d’index de global à local. Pour utiliser la mosaïque, appeler le [Extent::Tile, méthode](reference/extent-class.md#tile) sur le domaine de calcul dans le `parallel_for_each` (méthode) et utilisez un [tiled_index](../../parallel/amp/reference/tiled-index-class.md) objet dans l’expression lambda.

Dans les applications classiques, les éléments dans une mosaïque sont associés d’une certaine façon, et le code doit accéder et effectuer le suivi de valeurs sur la vignette. Utilisez le [tile_static, mot clé](../../cpp/tile-static-keyword.md) mot clé et le [tile_barrier::wait, méthode](reference/tile-barrier-class.md#wait) pour effectuer cette opération. Une variable qui a le **tile_static** mot clé a une étendue dans une mosaïque entière, et une instance de la variable est créée pour chaque mosaïque. Vous devez gérer la synchronisation de la vignette-thread l’accès à la variable. Le [tile_barrier::wait, méthode](reference/tile-barrier-class.md#wait) arrête l’exécution du thread actuel jusqu'à ce que tous les threads dans la mosaïque aient atteint l’appel à `tile_barrier::wait`. Vous pouvez accumuler des valeurs sur la vignette à l’aide de **tile_static** variables. Vous pouvez ensuite terminer tous les calculs qui requièrent l’accès à toutes les valeurs.

Le diagramme suivant représente un tableau à deux dimensions de données qui sont organisées en mosaïques d’échantillonnage.

![Indexer les valeurs dans une étendue en mosaïque](../../parallel/amp/media/camptiledgridexample.png "indexer les valeurs dans une étendue en mosaïque")

L’exemple de code suivant utilise les données d’échantillonnage à partir du diagramme précédent. Le code remplace chaque valeur dans la mosaïque par la moyenne des valeurs dans la vignette.

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

## <a name="math-libraries"></a>Bibliothèques de mathématiques

C++ AMP inclut deux bibliothèques mathématiques. La bibliothèque double précision dans le [Concurrency::precise_math Namespace](../../parallel/amp/reference/concurrency-precise-math-namespace.md) fournit la prise en charge des fonctions de double précision. Il prend également en charge pour les fonctions simple précision, bien que la prise en charge double précision sur le matériel est toujours requis. Il est conforme à la [spécification C99 (ISO/iec9899)](https://go.microsoft.com/fwlink/p/?linkid=225887). L’accélérateur doit prendre en charge double précision complète. Vous pouvez déterminer si l’opération est en vérifiant la valeur de la [Accelerator::supports_double_precision, données membres](reference/accelerator-class.md#supports_double_precision). La bibliothèque mathématique rapide, dans le [Concurrency::fast_math Namespace](../../parallel/amp/reference/concurrency-fast-math-namespace.md), contient un autre ensemble de fonctions mathématiques. Ces fonctions, qui prennent uniquement en charge `float` opérandes, s’exécutent plus rapidement, mais ne sont pas aussi précises que celles dans la bibliothèque mathématiques double précision. Les fonctions sont contenues dans le \<amp_math.h > fichier d’en-tête et tous sont déclarées avec `restrict(amp)`. Les fonctions dans le \<cmath > fichier d’en-tête sont importés dans les deux le `fast_math` et `precise_math` espaces de noms. Le **restreindre** mot clé est utilisé pour distinguer la \<cmath > version et la version C++ AMP. Le code suivant calcule le logarithme en base 10, à l’aide de la méthode rapide, de chaque valeur qui se trouve dans le domaine de calcul.

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

C++ AMP inclut une bibliothèque de graphiques qui est conçue pour la programmation graphique accélérée. Cette bibliothèque est utilisée uniquement sur les appareils qui prennent en charge des fonctionnalités graphiques natives. Les méthodes sont dans le [Concurrency::graphics Namespace](../../parallel/amp/reference/concurrency-graphics-namespace.md) et sont contenues dans le \<amp_graphics.h > fichier d’en-tête. Les composants clés de la bibliothèque de graphiques sont :

- [texture, classe](../../parallel/amp/reference/texture-class.md): Vous pouvez utiliser la classe de texture pour créer des textures à partir de la mémoire ou d’un fichier. Les textures ressemblent aux tableaux car ils contiennent des données, et elles ressemblent aux conteneurs dans la bibliothèque C++ Standard en ce qui concerne l’affectation et construction de copie. Pour plus d’informations, consultez [Conteneurs de la bibliothèque standard C++](../../standard-library/stl-containers.md). Les paramètres du modèle pour la `texture` classe sont le type d’élément et le rang. Le rang peut être 1, 2 ou 3. Le type d’élément peut être un des types vectoriels courts décrits plus loin dans cet article.

- [writeonly_texture_view, classe](../../parallel/amp/reference/writeonly-texture-view-class.md): Fournit l’accès en écriture seule à une texture.

- Bibliothèque de vecteurs courts : Définit un ensemble de types de vecteurs courts de longueur 2, 3 et 4 sont basés sur **int**, `uint`, **float**, **double**, [norm](../../parallel/amp/reference/norm-class.md), ou [unorm](../../parallel/amp/reference/unorm-class.md).

## <a name="universal-windows-platform-uwp-apps"></a>Applications de la plateforme Windows universelle (UWP)

Comme les autres bibliothèques C++, vous pouvez utiliser C++ AMP dans vos applications UWP. Ces articles décrivent comment inclure du code C++ AMP dans les applications qui est créé à l’aide de C++, c#, Visual Basic ou JavaScript :

- [Utilisation de C++ AMP dans les applications UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)

- [Procédure pas à pas : Création d’un composant de base Windows Runtime en C++ et l’appeler à partir de JavaScript](https://go.microsoft.com/fwlink/p/?linkid=249077)

- [Bing Maps Trip Optimizer, une application de la fenêtre Store en JavaScript et C++](https://go.microsoft.com/fwlink/p/?linkid=249078)

- [Comment utiliser C++ AMP à partir de c# à l’aide de l’exécution de Windows](https://go.microsoft.com/fwlink/p/?linkid=249080)

- [Comment utiliser C++ AMP à partir de c#](https://go.microsoft.com/fwlink/p/?linkid=249081)

- [Appel à des fonctions natives à partir de code managé](../../dotnet/calling-native-functions-from-managed-code.md)

## <a name="c-amp-and-concurrency-visualizer"></a>C++ AMP et visualiseur concurrentiel

Le visualiseur concurrentiel prend en charge pour l’analyse des performances du code C++ AMP. Ces articles décrivent ces fonctionnalités :

- [Graphique d’activité GPU](/visualstudio/profiling/gpu-activity-graph)

- [Activité GPU (pagination)](/visualstudio/profiling/gpu-activity-paging)

- [Activité GPU (ce processus)](/visualstudio/profiling/gpu-activity-this-process)

- [Activité GPU (autres processus)](/visualstudio/profiling/gpu-activity-other-processes)

- [Canaux (vue Threads)](/visualstudio/profiling/channels-threads-view)

- [Analyse du Code C++ AMP avec le visualiseur concurrentiel](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)

## <a name="performance-recommendations"></a>Recommandations relatives aux performances

Modulo et la division d’entiers non signés sont considérablement plus performants que le modulo et la division des entiers signés. Nous vous recommandons d’utiliser des entiers non signés lorsque cela est possible.

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Syntaxe d’expression lambda](../../cpp/lambda-expression-syntax.md)<br/>
[Référence (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Programmation parallèle en Code natif Blog](https://go.microsoft.com/fwlink/p/?linkid=238472)
