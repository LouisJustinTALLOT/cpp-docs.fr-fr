---
title: Utilisation des mosaïques
ms.date: 11/19/2018
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
ms.openlocfilehash: edef9154b0c4da6f53c8ac40ee84e55e9b38a9b7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228464"
---
# <a name="using-tiles"></a>Utilisation des mosaïques

Vous pouvez utiliser la mosaïque pour optimiser l’accélération de votre application. La mosaïque divise les threads en sous-ensembles rectangulaires égaux ou en *mosaïques*. Si vous utilisez une taille de vignette et un algorithme en mosaïque appropriés, vous pouvez obtenir une accélération supplémentaire à partir de votre code C++ AMP. Les composants de base de la mosaïque sont les suivants :

- `tile_static`variables. Le principal avantage de la mosaïque est le gain de performance de l' `tile_static` accès. L’accès aux données en `tile_static` mémoire peut être beaucoup plus rapide que l’accès aux données dans l’espace global ( `array` ou les `array_view` objets). Une instance d’une `tile_static` variable est créée pour chaque vignette, et tous les threads de la mosaïque ont accès à la variable. Dans un algorithme en mosaïque classique, les données sont copiées en `tile_static` mémoire une seule fois à partir de la mémoire globale, puis consultées plusieurs fois à partir de la `tile_static` mémoire.

- [tile_barrier :: Wait, méthode](reference/tile-barrier-class.md#wait). Un appel à `tile_barrier::wait` suspend l’exécution du thread actuel jusqu’à ce que tous les threads de la même mosaïque atteignent l’appel à `tile_barrier::wait` . Vous ne pouvez pas garantir l’ordre dans lequel les threads s’exécuteront, seulement qu’aucun thread de la mosaïque ne s’exécutera après l’appel à `tile_barrier::wait` jusqu’à ce que tous les threads aient atteint l’appel. Cela signifie qu’à l’aide de la `tile_barrier::wait` méthode, vous pouvez effectuer des tâches en mosaïque par vignette plutôt qu’en fonction du thread par thread. Un algorithme de mosaïque classique a du code pour initialiser la `tile_static` mémoire pour la vignette entière, suivie d’un appel à `tile_barrier::wait` . Le code qui suit `tile_barrier::wait` contient des calculs qui requièrent l’accès à toutes les `tile_static` valeurs.

- Indexation locale et globale. Vous avez accès à l’index du thread par rapport à l’ensemble `array_view` ou à l' `array` objet et à l’index par rapport à la vignette. L’utilisation de l’index local peut faciliter la lecture et le débogage de votre code. En règle générale, vous utilisez l’indexation locale pour accéder aux `tile_static` variables et l’indexation globale pour accéder aux `array` `array_view` variables et.

- [tiled_extent](../../parallel/amp/reference/tiled-extent-class.md) classe et [tiled_index classe](../../parallel/amp/reference/tiled-index-class.md). Vous utilisez un `tiled_extent` objet au lieu d’un `extent` objet dans l' `parallel_for_each` appel. Vous utilisez un `tiled_index` objet au lieu d’un `index` objet dans l' `parallel_for_each` appel.

Pour tirer parti de la mosaïque, votre algorithme doit partitionner le domaine de calcul en mosaïques, puis copier les données de vignette dans `tile_static` des variables pour un accès plus rapide.

## <a name="example-of-global-tile-and-local-indices"></a>Exemple d’index globaux, de mosaïques et locaux

Le diagramme suivant représente une matrice 8x9 de données qui est organisée en mosaïques 2x3.

![8&#45;par&#45;matrice 9 divisée en 2&#45;par&#45;3 mosaïques](../../parallel/amp/media/usingtilesmatrix.png "8&#45;par&#45;matrice 9 divisée en 2&#45;par&#45;3 mosaïques")

L’exemple suivant affiche les index globaux, de mosaïque et locaux de cette matrice en mosaïque. Un `array_view` objet est créé à l’aide d’éléments de type `Description` . Le `Description` contient les index globaux, de mosaïque et locaux de l’élément dans la matrice. Le code dans l’appel à `parallel_for_each` définit les valeurs des index globaux, de mosaïque et locaux de chaque élément. La sortie affiche les valeurs dans les `Description` structures.

```cpp
#include <iostream>
#include <iomanip>
#include <Windows.h>
#include <amp.h>
using namespace concurrency;

const int ROWS = 8;
const int COLS = 9;

// tileRow and tileColumn specify the tile that each thread is in.
// globalRow and globalColumn specify the location of the thread in the array_view.
// localRow and localColumn specify the location of the thread relative to the tile.
struct Description {
    int value;
    int tileRow;
    int tileColumn;
    int globalRow;
    int globalColumn;
    int localRow;
    int localColumn;
};

// A helper function for formatting the output.
void SetConsoleColor(int color) {
    int colorValue = (color == 0)  4 : 2;
    SetConsoleTextAttribute(GetStdHandle(STD_OUTPUT_HANDLE), colorValue);
}

// A helper function for formatting the output.
void SetConsoleSize(int height, int width) {
    COORD coord;

    coord.X = width;
    coord.Y = height;
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);

    SMALL_RECT* rect = new SMALL_RECT();
    rect->Left = 0;
    rect->Top = 0;
    rect->Right = width;
    rect->Bottom = height;
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);
}

// This method creates an 8x9 matrix of Description structures.
// In the call to parallel_for_each, the structure is updated
// with tile, global, and local indices.
void TilingDescription() {
    // Create 72 (8x9) Description structures.
    std::vector<Description> descs;
    for (int i = 0; i < ROWS * COLS; i++) {
        Description d = {i, 0, 0, 0, 0, 0, 0};
        descs.push_back(d);
    }

    // Create an array_view from the Description structures.
    extent<2> matrix(ROWS, COLS);
    array_view<Description, 2> descriptions(matrix, descs);

    // Update each Description with the tile, global, and local indices.
    parallel_for_each(descriptions.extent.tile< 2, 3>(),
        [=] (tiled_index< 2, 3> t_idx) restrict(amp)
    {
        descriptions[t_idx].globalRow = t_idx.global[0];
        descriptions[t_idx].globalColumn = t_idx.global[1];
        descriptions[t_idx].tileRow = t_idx.tile[0];
        descriptions[t_idx].tileColumn = t_idx.tile[1];
        descriptions[t_idx].localRow = t_idx.local[0];
        descriptions[t_idx].localColumn= t_idx.local[1];
    });

    // Print out the Description structure for each element in the matrix.
    // Tiles are displayed in red and green to distinguish them from each other.
    SetConsoleSize(100, 150);
    for (int row = 0; row < ROWS; row++) {
        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Value: " << std::setw(2) << descriptions(row, column).value << "      ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Tile:   " << "(" << descriptions(row, column).tileRow << "," << descriptions(row, column).tileColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Global: " << "(" << descriptions(row, column).globalRow << "," << descriptions(row, column).globalColumn << ")  ";
        }
        std::cout << "\n";

        for (int column = 0; column < COLS; column++) {
            SetConsoleColor((descriptions(row, column).tileRow + descriptions(row, column).tileColumn) % 2);
            std::cout << "Local:  " << "(" << descriptions(row, column).localRow << "," << descriptions(row, column).localColumn << ")  ";
        }
        std::cout << "\n";
        std::cout << "\n";
    }
}

int main() {
    TilingDescription();
    char wait;
    std::cin >> wait;
}
```

Le travail principal de l’exemple se trouve dans la définition de l' `array_view` objet et l’appel à `parallel_for_each` .

1. Le vecteur de `Description` structures est copié dans un `array_view` objet 8x9.

2. La `parallel_for_each` méthode est appelée avec un `tiled_extent` objet en tant que domaine de calcul. L' `tiled_extent` objet est créé en appelant la `extent::tile()` méthode de la `descriptions` variable. Les paramètres de type de l’appel à `extent::tile()` , `<2,3>` , spécifient que les vignettes 2x3 sont créées. Par conséquent, la matrice 8x9 est présentée en mosaïque sur 12 vignettes, quatre lignes et trois colonnes.

3. La `parallel_for_each` méthode est appelée à l’aide d’un `tiled_index<2,3>` objet ( `t_idx` ) comme index. Les paramètres de type de l’index ( `t_idx` ) doivent correspondre aux paramètres de type du domaine de calcul ( `descriptions.extent.tile< 2, 3>()` ).

4. Lorsque chaque thread est exécuté, l’index `t_idx` retourne des informations sur la mosaïque dans laquelle le thread se trouve ( `tiled_index::tile` propriété) et l’emplacement du thread dans la vignette ( `tiled_index::local` propriété).

## <a name="tile-synchronizationtile_static-and-tile_barrierwait"></a>Synchronisation des vignettes : tile_static et tile_barrier :: wait

L’exemple précédent illustre la disposition des vignettes et les index, mais n’est pas très utile.  La mosaïque devient utile lorsque les vignettes font partie intégrante de l’algorithme et exploitent des `tile_static` variables. Étant donné que tous les threads d’une vignette ont accès aux `tile_static` variables, les appels à `tile_barrier::wait` sont utilisés pour synchroniser l’accès aux `tile_static` variables. Bien que tous les threads d’une vignette aient accès aux `tile_static` variables, il n’y a pas d’ordre garanti d’exécution des threads dans la vignette. L’exemple suivant montre comment utiliser des `tile_static` variables et la `tile_barrier::wait` méthode pour calculer la valeur moyenne de chaque vignette. Voici les clés pour comprendre l’exemple :

1. Le rawData est stocké dans une matrice de l’de l'.

2. La taille de la vignette est 2x2. Cela crée une grille 4x4 de vignettes et les moyennes peuvent être stockées dans une matrice 4x4 à l’aide d’un `array` objet. Il n’existe qu’un nombre limité de types que vous pouvez capturer par référence dans une fonction restreinte à AMP. La `array` classe est l’une d’elles.

3. La taille de la matrice et la taille de l’échantillon sont définies à l’aide d' `#define` instructions, car les paramètres de type de `array` ,, `array_view` `extent` et `tiled_index` doivent être des valeurs constantes. Vous pouvez également utiliser des `const int static` déclarations. En guise d’avantage supplémentaire, il est facile de modifier la taille de l’échantillon pour calculer la moyenne sur des vignettes 4x4.

4. Un `tile_static` tableau de valeurs float de 2x2 est déclaré pour chaque vignette. Bien que la déclaration se trouve dans le chemin de code pour chaque thread, un seul tableau est créé pour chaque vignette dans la matrice.

5. Une ligne de code permet de copier les valeurs de chaque vignette dans le `tile_static` tableau. Pour chaque thread, une fois que la valeur est copiée dans le tableau, l’exécution sur le thread s’arrête en raison de l’appel à `tile_barrier::wait` .

6. Lorsque tous les threads d’une mosaïque ont atteint le cloisonnement, la moyenne peut être calculée. Étant donné que le code s’exécute pour chaque thread, il existe une `if` instruction qui calcule uniquement la moyenne sur un thread. La moyenne est stockée dans la variable Averages. Le cloisonnement est essentiellement la construction qui contrôle les calculs par vignette, de la même façon que vous pouvez utiliser une **`for`** boucle.

7. Les données de la `averages` variable, car il s’agit d’un `array` objet, doivent être recopiées sur l’hôte. Cet exemple utilise l’opérateur Vector conversion.

8. Dans l’exemple complet, vous pouvez modifier l’échantillonnage à 4 et le code s’exécute correctement sans aucune autre modification.

```cpp
#include <iostream>
#include <amp.h>
using namespace concurrency;

#define SAMPLESIZE 2
#define MATRIXSIZE 8
void SamplingExample() {

    // Create data and array_view for the matrix.
    std::vector<float> rawData;
    for (int i = 0; i < MATRIXSIZE * MATRIXSIZE; i++) {
        rawData.push_back((float)i);
    }
    extent<2> dataExtent(MATRIXSIZE, MATRIXSIZE);
    array_view<float, 2> matrix(dataExtent, rawData);

    // Create the array for the averages.
    // There is one element in the output for each tile in the data.
    std::vector<float> outputData;
    int outputSize = MATRIXSIZE / SAMPLESIZE;
    for (int j = 0; j < outputSize * outputSize; j++) {
        outputData.push_back((float)0);
    }
    extent<2> outputExtent(MATRIXSIZE / SAMPLESIZE, MATRIXSIZE / SAMPLESIZE);
    array<float, 2> averages(outputExtent, outputData.begin(), outputData.end());

    // Use tiles that are SAMPLESIZE x SAMPLESIZE.
    // Find the average of the values in each tile.
    // The only reference-type variable you can pass into the parallel_for_each call
    // is a concurrency::array.
    parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
        [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
    {
        // Copy the values of the tile into a tile-sized array.
        tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
        tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

        // Wait for the tile-sized array to load before you calculate the average.
        t_idx.barrier.wait();

        // If you remove the if statement, then the calculation executes for every
        // thread in the tile, and makes the same assignment to averages each time.
        if (t_idx.local[0] == 0 && t_idx.local[1] == 0) {
            for (int trow = 0; trow < SAMPLESIZE; trow++) {
                for (int tcol = 0; tcol < SAMPLESIZE; tcol++) {
                    averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
                }
            }
            averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE * SAMPLESIZE);
        }
    });

    // Print out the results.
    // You cannot access the values in averages directly. You must copy them
    // back to a CPU variable.
    outputData = averages;
    for (int row = 0; row < outputSize; row++) {
        for (int col = 0; col < outputSize; col++) {
            std::cout << outputData[row*outputSize + col] << " ";
        }
        std::cout << "\n";
    }
    // Output for SAMPLESIZE = 2 is:
    //  4.5  6.5  8.5 10.5
    // 20.5 22.5 24.5 26.5
    // 36.5 38.5 40.5 42.5
    // 52.5 54.5 56.5 58.5

    // Output for SAMPLESIZE = 4 is:
    // 13.5 17.5
    // 45.5 49.5
}

int main() {
    SamplingExample();
}
```

## <a name="race-conditions"></a>Conditions de concurrence

Il peut être tentant de créer une `tile_static` variable nommée `total` et d’incrémenter cette variable pour chaque thread, comme suit :

```cpp
// Do not do this.
tile_static float total;
total += matrix[t_idx];
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
```

Le premier problème de cette approche est que les `tile_static` variables ne peuvent pas avoir d’initialiseurs. Le deuxième problème est qu’il existe une condition de concurrence sur l’assignation à `total` , car tous les threads de la mosaïque ont accès à la variable dans aucun ordre particulier. Vous pouvez programmer un algorithme pour autoriser un seul thread à accéder au total à chaque barrière, comme indiqué ci-dessous. Toutefois, cette solution n’est pas extensible.

```cpp
// Do not do this.
tile_static float total;
if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
    total = matrix[t_idx];
}
t_idx.barrier.wait();

if (t_idx.local[0] == 0&& t_idx.local[1] == 1) {
    total += matrix[t_idx];
}
t_idx.barrier.wait();

// etc.
```

## <a name="memory-fences"></a>Limites de mémoire

Il existe deux types d’accès à la mémoire qui doivent être synchronisés : l’accès à la mémoire global et `tile_static` l’accès à la mémoire. Un `concurrency::array` objet alloue uniquement de la mémoire globale. Un `concurrency::array_view` peut faire référence à la mémoire globale, `tile_static` à la mémoire, ou aux deux, en fonction de la façon dont il a été construit.  Il existe deux types de mémoire qui doivent être synchronisées :

- mémoire globale

- `tile_static`

Une *barrière de mémoire* garantit que les accès mémoire sont disponibles pour d’autres threads dans la vignette de thread, et que les accès à la mémoire sont exécutés en fonction de l’ordre du programme. Pour garantir cela, les compilateurs et les processeurs ne réorganisent pas les lectures et les écritures dans la clôture. Dans C++ AMP, une barrière de mémoire est créée par un appel à l’une des méthodes suivantes :

- [tile_barrier :: Wait, méthode](reference/tile-barrier-class.md#wait): crée une clôture autour de global et de la `tile_static` mémoire.

- [tile_barrier :: Wait_with_all_memory_fence méthode](reference/tile-barrier-class.md#wait_with_all_memory_fence): crée une barrière autour de la mémoire globale et de la `tile_static` mémoire.

- [tile_barrier :: Wait_with_global_memory_fence méthode](reference/tile-barrier-class.md#wait_with_global_memory_fence): crée une limite autour de la mémoire globale uniquement.

- [tile_barrier :: Wait_with_tile_static_memory_fence méthode](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): crée une limite autour de la `tile_static` mémoire uniquement.

L’appel de la clôture spécifique dont vous avez besoin peut améliorer les performances de votre application. Le type de cloisonnement affecte la façon dont le compilateur et les instructions de réorganisation du matériel. Par exemple, si vous utilisez une barrière de mémoire globale, elle s’applique uniquement aux accès à la mémoire globale et, par conséquent, le compilateur et le matériel peuvent réorganiser les lectures et les écritures dans `tile_static` des variables sur les deux côtés de la clôture.

Dans l’exemple suivant, la barrière synchronise les écritures dans `tileValues` , une `tile_static` variable. Dans cet exemple, `tile_barrier::wait_with_tile_static_memory_fence` est appelé à la place de `tile_barrier::wait` .

```cpp
// Using a tile_static memory fence.
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),
    [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)
{
    // Copy the values of the tile into a tile-sized array.
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];

    // Wait for the tile-sized array to load before calculating the average.
    t_idx.barrier.wait_with_tile_static_memory_fence();

    // If you remove the if statement, then the calculation executes
    // for every thread in the tile, and makes the same assignment to
    // averages each time.
    if (t_idx.local[0] == 0&& t_idx.local[1] == 0) {
        for (int trow = 0; trow <SAMPLESIZE; trow++) {
            for (int tcol = 0; tcol <SAMPLESIZE; tcol++) {
                averages(t_idx.tile[0],t_idx.tile[1]) += tileValues[trow][tcol];
            }
        }
    averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);
    }
});
```

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Mot clé tile_static](../../cpp/tile-static-keyword.md)
