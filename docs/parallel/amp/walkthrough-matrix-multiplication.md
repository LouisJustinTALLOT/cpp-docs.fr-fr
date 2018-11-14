---
title: 'Procédure pas à pas : Multiplication des matrices'
ms.date: 11/06/2018
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: d9516cf79b738ec03dd98133a4603b47f75eb2c8
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2018
ms.locfileid: "51327107"
---
# <a name="walkthrough-matrix-multiplication"></a>Procédure pas à pas : Multiplication des matrices

Cette procédure pas à pas montre comment utiliser C++ AMP pour accélérer l’exécution de la multiplication de matrice. Deux algorithmes sont présentés sans mosaïque et l’autre avec la mosaïque.

## <a name="prerequisites"></a>Prérequis

Avant de commencer :

- Lecture [présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md).

- Lecture [à l’aide de vignettes](../../parallel/amp/using-tiles.md).

- Vérifiez que Windows 7, Windows 8, Windows Server 2008 R2 ou Windows Server 2012 est installé sur votre ordinateur.

### <a name="to-create-the-project"></a>Pour créer le projet

1. Dans la barre de menus dans Visual Studio, choisissez **fichier** > **New** > **projet**.

1. Sous **installé** dans le volet Modèles, sélectionnez **Visual C++**.

1. Sélectionnez **projet vide**, entrez *MatrixMultiply* dans le **nom** zone, puis choisissez le **OK** bouton.

1. Choisissez le bouton **Suivant**.

1. Dans **l’Explorateur de solutions**, ouvrez le menu contextuel pour **fichiers sources**, puis choisissez **ajouter** > **un nouvel élément**.

1. Dans le **ajouter un nouvel élément** boîte de dialogue, sélectionnez **fichier C++ (.cpp)**, entrez *MatrixMultiply.cpp* dans le **nom** zone, puis choisissez le  **Ajouter** bouton.

## <a name="multiplication-without-tiling"></a>Multiplication sans mosaïque

Dans cette section, prenez en compte la multiplication de deux matrices, A et B, qui sont définis comme suit :

![3&#45;par&#45;matrice 2](../../parallel/amp/media/campmatrixanontiled.png "campmatrixanontiled")

![2&#45;par&#45;matrice 3](../../parallel/amp/media/campmatrixbnontiled.png "campmatrixbnontiled")

A est une matrice 3 x 2 et B est une matrice 2 x 3. Le produit de multipliant A par B est la matrice 3 x 3 suivante. Le produit est calculé en multipliant les lignes de A, en fonction des colonnes de B élément par élément.

![3&#45;par&#45;matrice 3](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;par&#45;matrice 3")

### <a name="to-multiply-without-using-c-amp"></a>À multiplier sans utiliser C++ AMP

1. Ouvrez MatrixMultiply.cpp et utilisez le code suivant pour remplacer le code existant.

```cpp
#include <iostream>

void MultiplyWithOutAMP() {
    int aMatrix[3][2] = {{1, 4}, {2, 5}, {3, 6}};
    int bMatrix[2][3] = {{7, 8, 9}, {10, 11, 12}};
    int product[3][3] = {{0, 0, 0}, {0, 0, 0}, {0, 0, 0}};

    for (int row = 0; row < 3; row++) {
        for (int col = 0; col < 3; col++) {
            // Multiply the row of A by the column of B to get the row, column of product.
            for (int inner = 0; inner < 2; inner++) {
                product[row][col] += aMatrix[row][inner] * bMatrix[inner][col];
            }
            std::cout << product[row][col] << "  ";
        }
        std::cout << "\n";
    }
}

void main() {
    MultiplyWithOutAMP();
    getchar();
}
```

   L’algorithme est une implémentation simple de la définition de la multiplication de matrice. Il n’utilise pas tous les algorithmes parallèles ou multithreads pour réduire le temps de calcul.

1. Dans la barre de menus, sélectionnez **Fichier** > **Enregistrer tout**.

1. Choisissez le **F5** raccourci clavier pour démarrer le débogage et de vérifier que la sortie est correcte.

1. Choisissez **entrée** pour quitter l’application.

### <a name="to-multiply-by-using-c-amp"></a>Multiplier par à l’aide de C++ AMP

1. Dans MatrixMultiply.cpp, ajoutez le code suivant avant le `main` (méthode).

```cpp
void MultiplyWithAMP() {
    int aMatrix[] = { 1, 4, 2, 5, 3, 6 };
    int bMatrix[] = { 7, 8, 9, 10, 11, 12 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    array_view<int, 2> a(3, 2, aMatrix);

    array_view<int, 2> b(2, 3, bMatrix);

    array_view<int, 2> product(3, 3, productMatrix);

    parallel_for_each(product.extent,
        [=] (index<2> idx) restrict(amp) {
            int row = idx[0];
            int col = idx[1];
            for (int inner = 0; inner <2; inner++) {
                product[idx] += a(row, inner)* b(inner, col);
            }
        });

    product.synchronize();

    for (int row = 0; row <3; row++) {
        for (int col = 0; col <3; col++) {
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

   Le code AMP ressemble au code non-AMP. L’appel à `parallel_for_each` démarre un thread pour chaque élément dans `product.extent`et remplace le `for` boucles pour les lignes et de colonnes. La valeur de la cellule à la ligne et la colonne est disponible dans `idx`. Vous pouvez accéder aux éléments d’un `array_view` objet à l’aide la `[]` opérateur et une variable d’index, ou le `()` opérateur et les variables de ligne et de colonne. L’exemple illustre les deux méthodes. Le `array_view::synchronize` méthode copie les valeurs de la `product` variable vers la `productMatrix` variable.

1. Ajoutez le code suivant `include` et `using` instructions en haut de MatrixMultiply.cpp.

```cpp
#include <amp.h>
using namespace concurrency;
```

1. Modifier le `main` méthode à appeler le `MultiplyWithAMP` (méthode).

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    getchar();
}
```

1. Choisissez le **Ctrl**+**F5** raccourci clavier pour démarrer le débogage et de vérifier que la sortie est correcte.

1. Choisissez le **espace** pour quitter l’application.

## <a name="multiplication-with-tiling"></a>Multiplication avec une disposition en mosaïque

Cette option est une technique dans laquelle vous partitionnez les données en sous-ensembles de taille égale, qui sont connus sous forme de vignettes. Trois choses modifier lorsque vous utilisez la mosaïque.

- Vous pouvez créer `tile_static` variables. Accès aux données dans `tile_static` espace peut être bien plus rapide que l’accès aux données dans l’espace global. Une instance d’un `tile_static` variable est créée pour chaque mosaïque et tous les threads dans la mosaïque ont accès à la variable. Le principal avantage de la mosaïque est le gain de performances en raison `tile_static` accès.

- Vous pouvez appeler la [tile_barrier::wait](reference/tile-barrier-class.md#wait) méthode pour arrêter tous les threads dans une seule vignette à une ligne de code spécifiée. Vous ne pouvez pas garantir l’ordre dans lequel les threads s’exécuteront, uniquement que tous les threads dans une seule vignette seront arrête à l’appel à `tile_barrier::wait` avant de continuer l’exécution.

- Vous avez accès à l’index du thread par rapport à l’intégralité de `array_view` objet et l’index relatif à la vignette. À l’aide de l’index local, vous pouvez faciliter votre code pour la lecture et le débogage.

Pour tirer parti des mosaïques dans une multiplication de matrice, l’algorithme doit partitionner la matrice en mosaïques et puis copier les données de mosaïque dans `tile_static` variables pour un accès plus rapide. Dans cet exemple, la matrice est partitionnée en rapports entre les sous-matrices de taille égale. Le produit se trouve en multipliant les rapports entre les sous-matrices. Les deux matrices et leur produit dans cet exemple sont :

![4&#45;par&#45;matrice 4](../../parallel/amp/media/campmatrixatiled.png "4&#45;par&#45;matrice 4 A")

![4&#45;par&#45;matrice 4](../../parallel/amp/media/campmatrixbtiled.png "4&#45;par&#45;matrice 4 B")

![4&#45;par&#45;matrice 4](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;par&#45;produit de la matrice 4")

Les matrices sont partitionnées en matrices quatre 2 x 2, qui sont définies comme suit :

![4&#45;par&#45;matrice 4 partitionné en 2&#45;par&#45;sub 2&#45;matrices](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;par&#45;matrice 4 partitionné en 2&#45;par&#45;sub 2&#45;matrices")

![4&#45;par&#45;matrice 4 partitionné en 2&#45;par&#45;sub 2&#45;matrices](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;par&#45;matrice 4 partitionné en 2&#45;par&#45;sub 2&#45;matrices")

Le produit de A et B peut désormais être écrite et calculée comme suit :

![4&#45;par&#45;matrice 4 partitionné en 2&#45;par&#45;sub 2&#45;matrices](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;par&#45;produit une matrice 4 de A et B")

Étant donné que matrices `a` via `h` sommes d'entre eux sont des matrices de 2 x 2 ainsi que les matrices de 2 x 2, tous les produits. Elle suit également que le produit de A et B est une matrice 4 x 4, comme prévu. Pour vérifier rapidement l’algorithme, calculer la valeur de l’élément dans la première ligne, la première colonne dans le produit. Dans l’exemple, qui est la valeur de l’élément dans la première ligne et la première colonne de `ae + bg`. Il vous suffit de calculer la première colonne, la première ligne de `ae` et `bg` pour chaque terme. Cette valeur pour `ae` est `(1 * 1) + (2 * 5) = 11`. La valeur de `bg` est `(3 * 1) + (4 * 5) = 23`. La valeur finale est `11 + 23 = 34`, laquelle est correcte.

Pour implémenter cet algorithme, le code :

- Utilise un `tiled_extent` au lieu de l’objet une `extent` de l’objet dans le `parallel_for_each` appeler.

- Utilise un `tiled_index` au lieu de l’objet une `index` de l’objet dans le `parallel_for_each` appeler.

- Crée `tile_static` variables devant contenir les rapports entre les sous-matrices.

- Utilise le `tile_barrier::wait` méthode pour arrêter les threads pour le calcul des produits des rapports entre les sous-matrices.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Multiplier par à l’aide de AMP et de disposition en mosaïque

1. Dans MatrixMultiply.cpp, ajoutez le code suivant avant le `main` (méthode).

```cpp
void MultiplyWithTiling() {
    // The tile size is 2.
    static const int TS = 2;

    // The raw data.
    int aMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int bMatrix[] = { 1, 2, 3, 4, 5, 6, 7, 8, 1, 2, 3, 4, 5, 6, 7, 8 };
    int productMatrix[] = { 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 };

    // Create the array_view objects.
    array_view<int, 2> a(4, 4, aMatrix);
    array_view<int, 2> b(4, 4, bMatrix);
    array_view<int, 2> product(4, 4, productMatrix);

    // Call parallel_for_each by using 2x2 tiles.
    parallel_for_each(product.extent.tile<TS, TS>(),
        [=] (tiled_index<TS, TS> t_idx) restrict(amp)
        {
            // Get the location of the thread relative to the tile (row, col)
            // and the entire array_view (rowGlobal, colGlobal).
            int row = t_idx.local[0];
            int col = t_idx.local[1];
            int rowGlobal = t_idx.global[0];
            int colGlobal = t_idx.global[1];
            int sum = 0;

            // Given a 4x4 matrix and a 2x2 tile size, this loop executes twice for each thread.
            // For the first tile and the first loop, it copies a into locA and e into locB.
            // For the first tile and the second loop, it copies b into locA and g into locB.
            for (int i = 0; i < 4; i += TS) {
                tile_static int locA[TS][TS];
                tile_static int locB[TS][TS];
                locA[row][col] = a(rowGlobal, col + i);
                locB[row][col] = b(row + i, colGlobal);
                // The threads in the tile all wait here until locA and locB are filled.
                t_idx.barrier.wait();

                // Return the product for the thread. The sum is retained across
                // both iterations of the loop, in effect adding the two products
                // together, for example, a*e.
                for (int k = 0; k < TS; k++) {
                    sum += locA[row][k] * locB[k][col];
                }

                // All threads must wait until the sums are calculated. If any threads
                // moved ahead, the values in locA and locB would change.
                t_idx.barrier.wait();
                // Now go on to the next iteration of the loop.
            }

            // After both iterations of the loop, copy the sum to the product variable by using the global location.
            product[t_idx.global] = sum;
        });

    // Copy the contents of product back to the productMatrix variable.
    product.synchronize();

    for (int row = 0; row <4; row++) {
        for (int col = 0; col <4; col++) {
            // The results are available from both the product and productMatrix variables.
            //std::cout << productMatrix[row*3 + col] << "  ";
            std::cout << product(row, col) << "  ";
        }
        std::cout << "\n";
    }
}
```

    This example is significantly different than the example without tiling. The code uses these conceptual steps:

    1. Copier les éléments de mosaïque [0,0] de `a` dans `locA`. Copier les éléments de mosaïque [0,0] de `b` dans `locB`. Notez que `product` est affichée en mosaïque, pas `a` et `b`. Par conséquent, vous utilisez des indices globaux pour accéder `a, b`, et `product`. L’appel à `tile_barrier::wait` est essentielle. Il arrête tous les threads dans la vignette jusqu'à ce que les deux `locA` et `locB` sont remplis.

    2. Multiplier `locA` et `locB` et placer les résultats dans `product`.

    3. Copier les éléments de mosaïque [0,1] de `a` dans `locA`. Copier les éléments de mosaïque [1,0] de `b` dans `locB`.

    4. Multiplier `locA` et `locB` et les ajouter aux résultats qui sont déjà dans `product`.

    5. La multiplication de vignette [0,0] est terminée.

    6. Répétez les quatre autres vignettes. Il est sans indexation spécifiquement pour les vignettes et les threads peuvent s’exécuter dans n’importe quel ordre. Comme chaque thread s’exécute, le `tile_static` variables sont créées en conséquence pour chaque mosaïque et l’appel à `tile_barrier::wait` contrôle le flux de programme.

    7. Lorsque vous examinez attentivement l’algorithme, notez que chaque sous-matrice est chargé dans un `tile_static` mémoire deux fois. Ce transfert de données ne prend pas de temps. Toutefois, une fois les données dans `tile_static` mémoire, l’accès aux données est beaucoup plus rapide. Calculer les produits requiert un accès répété aux valeurs dans les rapports entre les sous-matrices, étant donné un gain de performances globales. Pour chaque algorithme, l’expérimentation est nécessaire pour rechercher l’algorithme optimal et de taille de la mosaïque.

         Dans les exemples non-AMP et non de vignette, chaque élément de A et B est accessible à quatre fois à partir de la mémoire globale pour calculer le produit. Dans l’exemple de vignette, chaque élément est accessible à deux reprises à partir de la mémoire globale et quatre fois de la `tile_static` mémoire. Qui n’est pas un gain de performances significatifs. Toutefois, si A et B ont été 1 024 x 1 024 matrices et la taille de mosaïque étaient de 16, il n’y aurait un gain de performances significatifs. Dans ce cas, chaque élément sont copié dans `tile_static` mémoire que 16 fois et accessible à partir de `tile_static` mémoire 1024 fois.

2. Modifier la méthode main pour appeler le `MultiplyWithTiling` méthode, comme indiqué.

```cpp
void main() {
    MultiplyWithOutAMP();
    MultiplyWithAMP();
    MultiplyWithTiling();
    getchar();
}
```

3. Choisissez le **Ctrl**+**F5** raccourci clavier pour démarrer le débogage et de vérifier que la sortie est correcte.

4. Choisissez le **espace** barre pour quitter l’application.

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Procédure pas-à-pas : débogage d’une application C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)