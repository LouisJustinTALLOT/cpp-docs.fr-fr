---
title: "Utilisation des mosaïques | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: acb86a86-2b7f-43f1-8fcf-bcc79b21d9a8
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0cb598a5b0f87080a937218962037d849275d7bd
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="using-tiles"></a>Utilisation des mosaïques
Vous pouvez utiliser la disposition en mosaïque pour optimiser l’accélération de votre application. Mosaïque divise les threads en sous-ensembles rectangulaires égales ou *vignettes*. Si vous utilisez une taille de la vignette appropriée et un algorithme en mosaïque, vous pouvez obtenir davantage d’accélération à partir de votre code C++ AMP. Les composants de la mosaïque de base sont :  
  
- `tile_static`variables. Le principal avantage de mosaïque est le gain de performances à partir de `tile_static` accès. Accès aux données dans `tile_static` mémoire peut être considérablement plus rapide que l’accès aux données dans l’espace global (`array` ou `array_view` objets). Une instance d’un `tile_static` variable est créée pour chaque mosaïque, et tous les threads dans la vignette ont accès à la variable. Dans un algorithme en mosaïque par défaut, les données sont copiées dans `tile_static` mémoire qu’une seule fois à partir de la mémoire globale et ensuite accessibles autant de fois depuis le `tile_static` mémoire.  
  
- [tile_barrier::wait, méthode](reference/tile-barrier-class.md#wait). Un appel à `tile_barrier::wait` suspend l’exécution du thread actuel jusqu'à ce que tous les threads dans la vignette même atteint l’appel de `tile_barrier::wait`. Vous ne pouvez pas garantir l’ordre que les threads s’exécuteront, seulement qu’aucun thread de la vignette ne s’exécute après l’appel à `tile_barrier::wait` jusqu'à ce que tous les threads ont atteint l’appel. Cela signifie qu’à l’aide de la `tile_barrier::wait` (méthode), vous pouvez effectuer des tâches sur une base par vignette de vignette plutôt que sur une base par thread de threads. Un algorithme de disposition en mosaïque classique comporte du code pour initialiser le `tile_static` mémoire de la vignette entier suivi par un appel à `tile_barrer::wait`. Le code qui suit `tile_barrier::wait` contient des calculs qui requièrent l’accès à tous les `tile_static` valeurs.  

  
-   L’indexation local et global. Vous avez accès à l’index du thread par rapport à l’ensemble du `array_view` ou `array` objet et l’index par rapport à la vignette. À l’aide de l’index local peut rendre votre code plus facile à lire et à déboguer. En général, vous utilisez l’indexation local pour accéder à `tile_static` variables et à l’indexation globale pour accéder à `array` et `array_view` variables.  
  
- [tiled_extent, classe](../../parallel/amp/reference/tiled-extent-class.md) et [tiled_index, classe](../../parallel/amp/reference/tiled-index-class.md). Vous utilisez un `tiled_extent` au lieu de l’objet une `extent` de l’objet dans le `parallel_for_each` appeler. Vous utilisez un `tiled_index` au lieu de l’objet une `index` de l’objet dans le `parallel_for_each` appeler.  
  
 Pour tirer parti de mosaïque, votre algorithme doit être le domaine de calcul de la partition en mosaïques et puis copiez les données de mosaïque dans `tile_static` variables pour un accès plus rapide.  
  
## <a name="example-of-global-tile-and-local-indices"></a>Exemple de Global, mosaïque et Indices Local  
 Le diagramme suivant représente une matrice 8 x 9 de données qui sont organisées en mosaïques 2 x 3.  
  
 ![8 &#45; par &#45; matrice 9 divisée en 2 &#45; par &#45; 3 vignettes](../../parallel/amp/media/usingtilesmatrix.png "usingtilesmatrix")  
  
 L’exemple suivant affiche la vignette globale, et des indices locales de cet affichage en mosaïque des matrice. Un `array_view` objet est créé à l’aide des éléments de type `Description`. Le `Description` contient global, vignette, local et des index et l’élément dans la matrice. Le code dans l’appel à `parallel_for_each` définit les valeurs des globale, une vignette et un index local de chaque élément. La sortie affiche les valeurs dans le `Description` structures.  
  
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
    COORD coord; coord.X = width; coord.Y = height;  
    SetConsoleScreenBufferSize(GetStdHandle(STD_OUTPUT_HANDLE), coord);  
    SMALL_RECT* rect = new SMALL_RECT();  
    rect->Left = 0; rect->Top = 0; rect->Right = width; rect->Bottom = height;  
    SetConsoleWindowInfo(GetStdHandle(STD_OUTPUT_HANDLE), true, rect);  
}  
  
// This method creates an 8x9 matrix of Description structures. In the call to parallel_for_each, the structure is updated   
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
  
void main() {  
    TilingDescription();  
    char wait;  
    std::cin >> wait;  
}  
  
```  
  
 Le travail principal de l’exemple est dans la définition de la `array_view` objet et l’appel à `parallel_for_each`.  
  
1.  Le vecteur de `Description` structures est copié dans un 8 x 9 `array_view` objet.  
  
2.  Le `parallel_for_each` méthode est appelée avec un `tiled_extent` objet en tant que le domaine de calcul. Le `tiled_extent` objet est créé en appelant le `extent::tile()` méthode de la `descriptions` variable. Les paramètres de type de l’appel à `extent::tile()`, `<2,3>`, spécifiez que les mosaïques 2 x 3 sont créés. Par conséquent, la matrice 8 x 9 est affichée en mosaïque dans les 12 vignettes, quatre lignes et trois colonnes.  
  
3.  Le `parallel_for_each` méthode est appelée en utilisant un `tiled_index<2,3>` objet (`t_idx`) en tant que l’index. Les paramètres de type de l’index (`t_idx`) doivent correspondre les paramètres de type du domaine de calcul (`descriptions.extent.tile< 2, 3>()`).  
  
4.  Lors de l’exécution de chaque thread, l’index `t_idx` renvoie des informations sur la mosaïque, le thread est dans (`tiled_index::tile` propriété) et l’emplacement du thread dans la vignette (`tiled_index::local` propriété).  
  
## <a name="tile-synchronizationtilestatic-and-tilebarrierwait"></a>Vignette de synchronisation : tile_static et tile_barrier::wait  
 L’exemple précédent illustre la disposition en mosaïque et des index, mais n’est pas en soi très utiles.  Mosaïque devient utile quand les vignettes font partie intégrante de l’algorithme et les exploiter `tile_static` variables. Étant donné que tous les threads dans une vignette ont accès à `tile_static` variables, les appels à `tile_barrier::wait` sont utilisés pour synchroniser l’accès à la `tile_static` variables. Bien que tous les threads dans une vignette ont accès à la `tile_static` variables, il n’existe aucun ordre garanti d’exécution des threads dans la vignette. L’exemple suivant montre comment utiliser `tile_static` variables et la `tile_barrier::wait` méthode pour calculer la valeur moyenne de chaque vignette. Voici les clés à la compréhension de l’exemple :  
  
1.  Le rawData est stocké dans une matrice 8 x 8.  
  
2.  La taille de la vignette est 2 x 2. Cette opération crée une 4x4 grille de vignettes et les moyennes peuvent être stockées dans une matrice 4 x 4 en utilisant un `array` objet. Il existe uniquement un nombre limité de types que vous pouvez capturer par référence dans une fonction restreinte à AMP. La `array` classe est un d’eux.  
  
3.  La taille de la matrice et de la taille de l’échantillon sont définis à l’aide de `#define` instructions, car les paramètres de type à `array`, `array_view`, `extent`, et `tiled_index` doivent être des valeurs de constantes. Vous pouvez également utiliser `const int static` déclarations. Offre un autre avantage, c’est facile à modifier la taille d’échantillon pour calculer les vignettes de plus de 4 x 4 moyenne.  
  
4.  A `tile_static` tableau 2 x 2 de valeurs float est déclaré pour chaque mosaïque. Bien que la déclaration est dans le chemin d’accès du code pour chaque thread, un seul groupe est créé pour chaque mosaïque dans la matrice.  
  
5.  Il existe une ligne de code pour copier les valeurs dans chaque vignette pour le `tile_static` tableau. Pour chaque thread, une fois que la valeur est copiée dans le tableau, l’exécution sur le thread s’arrête en raison de l’appel à `tile_barrier::wait`.  
  
6.  Lorsque tous les threads dans une vignette ont atteint le cloisonnement, la moyenne peut être calculée. Étant donné que le code s’exécute pour chaque thread, il existe un `if` instruction uniquement calculer la moyenne sur un thread. La moyenne est stockée dans la variable de moyennes. Le cloisonnement est essentiellement la construction qui contrôle les calculs en mosaïque, que vous pouvez utiliser un `for` boucle.  
  
7.  Les données dans le `averages` variable, car il s’agit d’un `array` d’objet, doivent être copiés vers l’hôte. Cet exemple utilise l’opérateur de conversion de vecteur.  
  
8.  Dans l’exemple complet, vous pouvez modifier SAMPLESIZE à 4, et le code s’exécute correctement, sans aucune autre modification.  
  
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
    // Output for SAMPLESSIZE = 2 is:  
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
 Il peut être tentant de créer un `tile_static` variable nommée `total` et incrémente cette variable pour chaque thread, comme suit :  
  
```cpp  
// Do not do this.  
tile_static float total;  
total += matrix[t_idx];  
t_idx.barrier.wait();

averages(t_idx.tile[0],t_idx.tile[1]) /= (float) (SAMPLESIZE* SAMPLESIZE);

 
```  
  
 Le premier problème avec cette approche est que `tile_static` variables ne peuvent pas avoir d’initialiseurs. Le deuxième problème est qu’il existe une condition de concurrence sur l’affectation à `total`, car tous les threads dans la vignette ont accès à la variable dans aucun ordre particulier. Vous pouviez programmer un algorithme pour autoriser uniquement un seul thread accéder à chaque barrière, comme le montre l’illustration suivante. Toutefois, cette solution n’est pas extensible.  
  
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
 Il existe deux types d’accès à la mémoire qui doivent être synchronisées : accès à la mémoire globale et `tile_static` accès à la mémoire. A `concurrency::array` objet alloue uniquement la mémoire globale. A `concurrency::array_view` peut faire référence à la mémoire globale, `tile_static` mémoire, ou les deux, selon la façon dont il a été construit.  Il existe deux types de mémoire qui doivent être synchronisés :  
  
-   mémoire globale  
  
- `tile_static`  
  
 A *limite de mémoire* garantit que les accès sont disponibles à d’autres threads dans la vignette de thread de la mémoire et que les accès sont exécutées en fonction de l’ordre du programme de la mémoire. Pour ce faire, les compilateurs et les processeurs ne pas réordonnancer les lectures et écritures sur la plage de gestion. En C++ AMP, une limite de mémoire est créée par un appel à une des méthodes suivantes :  
  

- [tile_barrier::wait, méthode](reference/tile-barrier-class.md#wait): crée une limite autour de deux global et `tile_static` mémoire.  
  
- [tile_barrier::wait_with_all_memory_fence, méthode](reference/tile-barrier-class.md#wait_with_all_memory_fence): crée une limite autour de deux global et `tile_static` mémoire.  
  
- [tile_barrier::wait_with_global_memory_fence, méthode](reference/tile-barrier-class.md#wait_with_global_memory_fence): crée une clôture autour uniquement la mémoire globale.  
  
- [tile_barrier::wait_with_tile_static_memory_fence, méthode](reference/tile-barrier-class.md#wait_with_tile_static_memory_fence): crée une clôture autour du seul `tile_static` mémoire.  

  
 Appel de la plage de gestion spécifique dont vous avez besoin peut améliorer les performances de votre application. Le type de cloisonnement affecte la façon dont le compilateur et le matériel de réorganiser les instructions. Par exemple, si vous utilisez une limite de mémoire globale, il applique l’accès à la mémoire uniquement globaux et par conséquent, le compilateur et le matériel peuvent réorganiser les lit et écrit dans `tile_static` variables sur les deux côtés de la clôture.  
  
 Dans l’exemple suivant, le cloisonnement synchronise les écritures `tileValues`, un `tile_static` variable. Dans cet exemple, `tile_barrier::wait_with_tile_static_memory_fence` est appelée à la place de `tile_barrier::wait`.  
  
```cpp  
// Using a tile_static memory fence.  
parallel_for_each(matrix.extent.tile<SAMPLESIZE, SAMPLESIZE>(),  
 [=, &averages] (tiled_index<SAMPLESIZE, SAMPLESIZE> t_idx) restrict(amp)   
{ *// Copy the values of the tile into a tile-sized array.  
    tile_static float tileValues[SAMPLESIZE][SAMPLESIZE];  
    tileValues[t_idx.local[0]][t_idx.local[1]] = matrix[t_idx];  
 *// Wait for the tile-sized array to load before calculating the average.  
    t_idx.barrier.wait_with_tile_static_memory_fence();

 *// If you remove the if statement, then the calculation executes for every *// thread in the tile, and makes the same assignment to averages each time.  
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
 [C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)   
 [tile_static, mot clé](../../cpp/tile-static-keyword.md)

