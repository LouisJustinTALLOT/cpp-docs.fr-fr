---
title: 'Procédure pas à pas : Multiplication des matrices'
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: 6387e68304c7b1dbf0531729b7b73b519f40d159
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215866"
---
# <a name="walkthrough-matrix-multiplication"></a>Procédure pas à pas : Multiplication des matrices

Cette procédure pas à pas montre comment utiliser C++ AMP pour accélérer l’exécution de la multiplication de matrice. Deux algorithmes sont présentés : un sans mosaïque et un avec une mosaïque.

## <a name="prerequisites"></a>Prérequis

Avant de commencer :

- Lisez [C++ amp vue d’ensemble](../../parallel/amp/cpp-amp-overview.md).

- Lire [à l’aide de vignettes](../../parallel/amp/using-tiles.md).

- Assurez-vous que vous exécutez au moins Windows 7 ou Windows Server 2008 R2.

### <a name="to-create-the-project"></a>Pour créer le projet

Les instructions de création d’un nouveau projet varient en fonction de la version de Visual Studio que vous avez installée. Pour consulter la documentation de votre version par défaut de Visual Studio, utilisez le contrôle sélecteur de **version** . Elle se trouve en haut de la table des matières sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Pour créer le projet dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur ** C++ **, **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. Dans la liste filtrée des types de projets, choisissez **projet vide** , puis **suivant**. Dans la page suivante, entrez *MatrixMultiply* dans la zone **nom** pour spécifier un nom pour le projet, puis spécifiez l’emplacement du projet si vous le souhaitez.

   ![Nouvelle application console](../../build/media/mathclient-project-name-2019.png "Nouvelle application console")

1. Choisissez le bouton **Créer** pour créer le projet client.

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel des **fichiers sources**, puis choisissez **Ajouter** > **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **fichier C++ (. cpp)**, entrez *MatrixMultiply. cpp* dans la zone **nom** , puis choisissez le bouton **Ajouter** .

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>Pour créer un projet dans Visual Studio 2017 ou 2015

1. Dans la barre de menus de Visual Studio, choisissez **fichier** > **nouveau** > **projet**.

1. Sous **installé** dans le volet modèles, sélectionnez **Visual C++**.

1. Sélectionnez **projet vide**, entrez *MatrixMultiply* dans la zone **nom** , puis choisissez le bouton **OK** .

1. Choisissez le bouton **Suivant**.

1. Dans **Explorateur de solutions**, ouvrez le menu contextuel des **fichiers sources**, puis choisissez **Ajouter** > **un nouvel élément**.

1. Dans la boîte de dialogue **Ajouter un nouvel élément** , sélectionnez **fichier C++ (. cpp)**, entrez *MatrixMultiply. cpp* dans la zone **nom** , puis choisissez le bouton **Ajouter** .

::: moniker-end

## <a name="multiplication-without-tiling"></a>Multiplication sans mosaïque

Dans cette section, prenez en compte la multiplication de deux matrices, A et B, qui sont définies comme suit :

![3&#45;par&#45;2 matrice A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;par&#45;2 matrice A")

![2&#45;par&#45;3 matrice B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;par&#45;3 matrice B")

Un est une matrice 3 par 2 et B est une matrice 2 par 3. Le produit de la multiplication d’un par B est la matrice 3 par 3 suivante. Le produit est calculé en multipliant les lignes d’un par les colonnes de l’élément B par élément.

![3&#45;par&#45;3 matrice produit](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;par&#45;3 matrice produit")

### <a name="to-multiply-without-using-c-amp"></a>À multiplier sans utiliser C++ AMP

1. Ouvrez MatrixMultiply. cpp et utilisez le code suivant pour remplacer le code existant.

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

   int main() {
       MultiplyWithOutAMP();
       getchar();
   }
   ```

   L’algorithme est une implémentation simple de la définition de la multiplication de matrice. Elle n’utilise pas d’algorithmes parallèles ou de threads pour réduire le temps de calcul.

1. Dans la barre de menus, choisissez **fichier**  >  **enregistrer tout**.

1. Appuyez sur le raccourci clavier **F5** pour démarrer le débogage et vérifier que la sortie est correcte.

1. Appuyez sur **entrée** pour quitter l’application.

### <a name="to-multiply-by-using-c-amp"></a>Pour multiplier à l’aide de C++ AMP

1. Dans MatrixMultiply. cpp, ajoutez le code suivant avant la `main` méthode.

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

   Le code AMP ressemble au code non AMP. L’appel à `parallel_for_each` démarre un thread pour chaque élément dans `product.extent` et remplace les **`for`** boucles pour la ligne et la colonne. La valeur de la cellule au niveau de la ligne et de la colonne est disponible dans `idx` . Vous pouvez accéder aux éléments d’un `array_view` objet à l’aide de l' `[]` opérateur et d’une variable d’index, ou de l' `()` opérateur et des variables de ligne et de colonne. L’exemple illustre les deux méthodes. La `array_view::synchronize` méthode copie les valeurs de la `product` variable dans la `productMatrix` variable.

1. Ajoutez les `include` instructions et suivantes **`using`** en haut de MatrixMultiply. cpp.

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. Modifiez la `main` méthode pour appeler la `MultiplyWithAMP` méthode.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. Appuyez sur **Ctrl**le + raccourci clavier Ctrl**F5** pour démarrer le débogage et vérifier que la sortie est correcte.

1. Appuyez sur la **barre d’espace** pour quitter l’application.

## <a name="multiplication-with-tiling"></a>Multiplication avec mosaïque

La mosaïque est une technique dans laquelle vous partitionnez des données dans des sous-ensembles de taille égale, appelés vignettes. Trois choses changent lorsque vous utilisez la mosaïque.

- Vous pouvez créer des `tile_static` variables. L’accès aux données dans `tile_static` l’espace peut être beaucoup plus rapide que l’accès aux données dans l’espace global. Une instance d’une `tile_static` variable est créée pour chaque vignette, et tous les threads de la mosaïque ont accès à la variable. Le principal avantage de la mosaïque est le gain de performance dû à l' `tile_static` accès.

- Vous pouvez appeler la méthode [tile_barrier :: wait](reference/tile-barrier-class.md#wait) pour arrêter tous les threads d’une vignette à la ligne de code spécifiée. Vous ne pouvez pas garantir l’ordre dans lequel les threads s’exécuteront, seulement que tous les threads d’une vignette s’arrêteront lors de l’appel à `tile_barrier::wait` avant de continuer l’exécution.

- Vous avez accès à l’index du thread relatif à la totalité de l' `array_view` objet et à l’index relatif à la vignette. En utilisant l’index local, vous pouvez rendre votre code plus facile à lire et à déboguer.

Pour tirer parti de la mosaïque dans la multiplication de matrices, l’algorithme doit partitionner la matrice en mosaïques, puis copier les données de vignette dans `tile_static` des variables pour un accès plus rapide. Dans cet exemple, la matrice est partitionnée en sous-matrices de taille égale. Le produit est trouvé en multipliant les sous-matrices. Les deux matrices et leur produit dans cet exemple sont les suivants :

![4&#45;par&#45;4 matrice A](../../parallel/amp/media/campmatrixatiled.png "4&#45;par&#45;4 matrice A")

![4&#45;par&#45;4 matrice B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;par&#45;4 matrice B")

![4&#45;par&#45;4 matrice produit](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;par&#45;4 matrice produit")

Les matrices sont partitionnées en quatre matrices 2x2, qui sont définies comme suit :

![4&#45;par&#45;4 Matrix A partitionné en 2&#45;par&#45;2 matrices&#45;](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;par&#45;4 Matrix A partitionné en 2&#45;par&#45;2 matrices&#45;")

![4&#45;par&#45;4 matrice B partitionnée en 2&#45;par&#45;2 matrices&#45;](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;par&#45;4 matrice B partitionnée en 2&#45;par&#45;2 matrices&#45;")

Le produit de A et B peut désormais être écrit et calculé comme suit :

![4&#45;par&#45;4 matrice A B partitionné en 2&#45;par&#45;2 matrices&#45;](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;par&#45;4 matrice A B partitionné en 2&#45;par&#45;2 matrices&#45;")

Étant donné que `a` les matrices `h` sont des matrices 2x2, tous les produits et sommes de ceux-ci sont également des matrices 2x2. Elle suit également que le produit de A et B est une matrice 4x4, comme prévu. Pour vérifier rapidement l’algorithme, calculez la valeur de l’élément dans la première ligne, première colonne du produit. Dans l’exemple, il s’agit de la valeur de l’élément dans la première ligne et la première colonne de `ae + bg` . Il vous suffit de calculer la première colonne, la première ligne de `ae` et `bg` pour chaque terme. Cette valeur pour `ae` est `(1 * 1) + (2 * 5) = 11` . La valeur de `bg` est `(3 * 1) + (4 * 5) = 23`. La valeur finale est `11 + 23 = 34` , ce qui est correct.

Pour implémenter cet algorithme, le code :

- Utilise un `tiled_extent` objet au lieu d’un `extent` objet dans l' `parallel_for_each` appel.

- Utilise un `tiled_index` objet au lieu d’un `index` objet dans l' `parallel_for_each` appel.

- Crée `tile_static` des variables pour contenir les sous-matrices.

- Utilise la `tile_barrier::wait` méthode pour arrêter les threads pour le calcul des produits des sous-matrices.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Pour multiplier en utilisant AMP et une mosaïque

1. Dans MatrixMultiply. cpp, ajoutez le code suivant avant la `main` méthode.

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

   Cet exemple est très différent de l’exemple sans mosaïque. Le code utilise les étapes conceptuelles suivantes :
   1. Copiez les éléments de la vignette [0, 0] de `a` dans `locA` . Copiez les éléments de la vignette [0, 0] de `b` dans `locB` . Notez que `product` est en mosaïque, et non pas `a` et `b` . Par conséquent, vous utilisez des index globaux pour accéder à `a, b` , et `product` . L’appel à `tile_barrier::wait` est essentiel. Elle arrête tous les threads dans la vignette jusqu’à ce que `locA` et `locB` soient remplis.

   1. Multipliez `locA` et `locB` Placez les résultats dans `product` .

   1. Copiez les éléments de la vignette [0, 1] de `a` dans `locA` . Copiez les éléments de la vignette [1, 0] de `b` dans `locB` .

   1. Multipliez `locA` et `locB` Ajoutez-les aux résultats qui se trouvent déjà dans `product` .

   1. La multiplication de la vignette [0, 0] est terminée.

   1. Répétez cette opération pour les quatre autres vignettes. Il n’y a pas d’indexation spécifique pour les vignettes et les threads peuvent s’exécuter dans n’importe quel ordre. À mesure que chaque thread s’exécute, les `tile_static` variables sont créées pour chaque vignette de manière appropriée et l’appel à `tile_barrier::wait` contrôle le déroulement du programme.

   1. Lorsque vous examinez attentivement l’algorithme, Notez que chaque sous-matrice est chargée dans une `tile_static` mémoire deux fois. Ce transfert de données prend du temps. Toutefois, une fois que les données sont en `tile_static` mémoire, l’accès aux données est beaucoup plus rapide. Étant donné que le calcul des produits requiert un accès répété aux valeurs des sous-matrices, il existe un gain de performances global. Pour chaque algorithme, une expérimentation est nécessaire pour trouver la taille optimale de l’algorithme et de la vignette.

   Dans les exemples non-AMP et non-vignette, chaque élément de A et B est accessible quatre fois à partir de la mémoire globale pour calculer le produit. Dans l’exemple de vignette, chaque élément est accessible deux fois à partir de la mémoire globale et quatre fois à partir de la `tile_static` mémoire. Ce n’est pas un gain de performances significatif. Toutefois, si les matrices A et B étaient des matrices 1024x1024 et que la taille des vignettes était de 16, il y aurait un gain de performances significatif. Dans ce cas, chaque élément est copié en `tile_static` mémoire seulement 16 fois et est accessible à partir de la `tile_static` Mémoire 1024 fois.

1. Modifiez la méthode main pour appeler la `MultiplyWithTiling` méthode, comme indiqué.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. Appuyez sur **Ctrl**le + raccourci clavier Ctrl**F5** pour démarrer le débogage et vérifier que la sortie est correcte.

1. Appuyez sur la barre d' **espace** pour quitter l’application.

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Procédure pas à pas : débogage d’une application C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
