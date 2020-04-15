---
title: 'Procédure pas à pas : Multiplication des matrices'
ms.date: 04/23/2019
ms.assetid: 61172e8b-da71-4200-a462-ff3a908ab0cf
ms.openlocfilehash: f30f8dc235bf0e76c342bea26a35bcbb36cfa237
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366812"
---
# <a name="walkthrough-matrix-multiplication"></a>Procédure pas à pas : Multiplication des matrices

Cette procédure pas à pas étape étape par étape montre comment utiliser l’AMP de CMD pour accélérer l’exécution de la multiplication de la matrice. Deux algorithmes sont présentés, l’un sans carrelage et l’autre avec carrelage.

## <a name="prerequisites"></a>Prérequis

Avant de commencer :

- Lire [l’aperçu de l’AMP](../../parallel/amp/cpp-amp-overview.md).

- Lire [Utilisation des tuiles](../../parallel/amp/using-tiles.md).

- Assurez-vous que vous exécutez au moins Windows 7, ou Windows Server 2008 R2.

### <a name="to-create-the-project"></a>Pour créer le projet

Les instructions pour créer un nouveau projet varient selon la version de Visual Studio que vous avez installée. Pour voir la documentation de votre version préférée de Visual Studio, utilisez le contrôle du sélecteur **Version.** On le trouve en haut de la table des contenus sur cette page.

::: moniker range="vs-2019"

### <a name="to-create-the-project-in-visual-studio-2019"></a>Pour créer le projet dans Visual Studio 2019

1. Dans la barre de menus, choisissez **Fichier** > **Nouveau** > **Projet** pour ouvrir la boîte de dialogue **Créer un projet**.

1. En haut de la boîte de dialogue, définissez **Langage** sur ** C++ **, **Plateforme** sur **Windows** et **Type de projet** sur **Console**.

1. De la liste filtrée des types de projets, choisissez **Empty Project** puis choisissez **Next**. Dans la page suivante, entrez *MatrixMultiply* dans la boîte **nom** pour spécifier un nom pour le projet, et spécifiez l’emplacement du projet si désiré.

   ![Nouvelle application console](../../build/media/mathclient-project-name-2019.png "Nouvelle application console")

1. Choisissez le bouton **Créer** pour créer le projet client.

1. Dans **Solution Explorer**, ouvrez le menu raccourci pour les fichiers **Source,** puis choisissez **Ajouter** > **un nouvel article**.

1. Dans la boîte de dialogue **Add New Item,** sélectionnez **le fichier CMD (.cpp),** entrez *MatrixMultiply.cpp* dans la boîte **nom,** puis choisissez le bouton **Ajouter.**

::: moniker-end

::: moniker range="<=vs-2017"

### <a name="to-create-a-project-in-visual-studio-2017-or-2015"></a>Créer un projet en Visual Studio 2017 ou 2015

1. Sur la barre de menu de Visual Studio, choisissez **File** > **New** > **Project**.

1. Sous **Installé** dans la vitre des modèles, sélectionnez **Visual CM .**

1. Sélectionnez **Projet vide**, entrez *MatrixMultiply* dans la boîte **nom,** puis choisissez le bouton **OK.**

1. Choisissez le bouton **Suivant**.

1. Dans **Solution Explorer**, ouvrez le menu raccourci pour les fichiers **Source,** puis choisissez **Ajouter** > **un nouvel article**.

1. Dans la boîte de dialogue **Add New Item,** sélectionnez **le fichier CMD (.cpp),** entrez *MatrixMultiply.cpp* dans la boîte **nom,** puis choisissez le bouton **Ajouter.**

::: moniker-end

## <a name="multiplication-without-tiling"></a>Multiplication sans carrelage

Dans cette section, considérez la multiplication de deux matrices, A et B, qui sont définies comme suit :

![3&#45;par&#45;2 matrice A](../../parallel/amp/media/campmatrixanontiled.png "3&#45;par&#45;2 matrice A")

![2&#45;par&#45;3 matrice B](../../parallel/amp/media/campmatrixbnontiled.png "2&#45;par&#45;3 matrice B")

A est une matrice de 3 par 2 et B est une matrice de 2 par 3. Le produit de la multiplication A par B est la matrice suivante 3-par-3. Le produit est calculé en multipliant les lignes de A par les colonnes de L’élément B par élément.

![3&#45;par&#45;3 matrice de produits](../../parallel/amp/media/campmatrixproductnontiled.png "3&#45;par&#45;3 matrice de produits")

### <a name="to-multiply-without-using-c-amp"></a>Pour multiplier sans utiliser l’AMP de C

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

   int main() {
       MultiplyWithOutAMP();
       getchar();
   }
   ```

   L’algorithme est une mise en œuvre simple de la définition de la multiplication de la matrice. Il n’utilise pas d’algorithmes parallèles ou filetés pour réduire le temps de calcul.

1. Sur la barre de menu, choisissez **File** > **Save All**.

1. Choisissez le raccourci **clavier F5** pour commencer à débogage et vérifier que la sortie est correcte.

1. Choisissez **Entrez** pour sortir de l’application.

### <a name="to-multiply-by-using-c-amp"></a>Pour multiplier en utilisant l’AMP de C

1. Dans MatrixMultiply.cpp, ajoutez le `main` code suivant avant la méthode.

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

   Le code AMP ressemble au code non-AMP. L’appel `parallel_for_each` pour commencer un `product.extent`thread pour chaque `for` élément dans , et remplace les boucles pour la ligne et la colonne. La valeur de la cellule à la `idx`rangée et la colonne est disponible en . Vous pouvez accéder aux `array_view` éléments d’un objet en utilisant soit l’opérateur `[]` et une variable d’index, soit l’opérateur `()` et les variables de la ligne et de la colonne. L’exemple montre les deux méthodes. La `array_view::synchronize` méthode copie les `product` valeurs de `productMatrix` la variable à la variable.

1. Ajoutez ce `include` `using` qui suit et les déclarations en haut de MatrixMultiply.cpp.

   ```cpp
   #include <amp.h>
   using namespace concurrency;
   ```

1. Modifier `main` la méthode `MultiplyWithAMP` pour appeler la méthode.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       getchar();
   }
   ```

1. Appuyez sur le raccourci **clavier Ctrl**+**F5** pour commencer à débogage et vérifier que la sortie est correcte.

1. Appuyez sur le **Spacebar** pour sortir de l’application.

## <a name="multiplication-with-tiling"></a>Multiplication avec carrelage

Le carrelage est une technique dans laquelle vous divisez les données en sous-ensembles de taille égale, qui sont connus sous le nom de tuiles. Trois choses changent lorsque vous utilisez le carrelage.

- Vous pouvez `tile_static` créer des variables. L’accès `tile_static` aux données dans l’espace peut être beaucoup plus rapide que l’accès aux données dans l’espace mondial. Une instance `tile_static` d’une variable est créée pour chaque tuile, et tous les fils de la tuile ont accès à la variable. Le principal avantage du carrelage `tile_static` est le gain de performance dû à l’accès.

- Vous pouvez appeler le [tile_barrier::méthode d’attente](reference/tile-barrier-class.md#wait) pour arrêter tous les fils dans une tuile à une ligne de code spécifiée. Vous ne pouvez pas garantir l’ordre que les fils s’exécuteront, seulement que `tile_barrier::wait` tous les fils dans une tuile s’arrêtera à l’appel avant qu’ils continuent l’exécution.

- Vous avez accès à l’index du `array_view` thread par rapport à l’objet entier et à l’index par rapport à la tuile. En utilisant l’index local, vous pouvez rendre votre code plus facile à lire et à déboiffer.

Pour tirer parti du carrelage dans la multiplication de la matrice, l’algorithme doit diviser la matrice en tuiles, puis copier les données de tuiles en `tile_static` variables pour un accès plus rapide. Dans cet exemple, la matrice est divisée en sous-millions de taille égale. Le produit se trouve en multipliant les sous-millions. Les deux matrices et leur produit dans cet exemple sont :

![4&#45;par&#45;4 matrice A](../../parallel/amp/media/campmatrixatiled.png "4&#45;par&#45;4 matrice A")

![4&#45;par&#45;4 matrice B](../../parallel/amp/media/campmatrixbtiled.png "4&#45;par&#45;4 matrice B")

![4&#45;par&#45;4 matrice de produits](../../parallel/amp/media/campmatrixproducttiled.png "4&#45;par&#45;4 matrice de produits")

Les matrices sont divisées en quatre matrices 2x2, qui sont définies comme suit :

![4&#45;par&#45;4 matrice A cloisonnée en 2&#45;par&#45;2 matrices sous&#45;](../../parallel/amp/media/campmatrixapartitioned.png "4&#45;par&#45;4 matrice A cloisonnée en 2&#45;par&#45;2 matrices sous&#45;")

![4&#45;par&#45;4 matrice B divisée en 2&#45;par&#45;2 matrices sous&#45;](../../parallel/amp/media/campmatrixbpartitioned.png "4&#45;par&#45;4 matrice B divisée en 2&#45;par&#45;2 matrices sous&#45;")

Le produit de A et B peut maintenant être écrit et calculé comme suit :

![4&#45;par&#45;4 matrice A B divisée en 2&#45;par&#45;2 matrices sous&#45;](../../parallel/amp/media/campmatrixproductpartitioned.png "4&#45;par&#45;4 matrice A B divisée en 2&#45;par&#45;2 matrices sous&#45;")

Parce que `a` les `h` matrices à travers sont 2x2 matrices, tous les produits et les sommes d’entre eux sont également 2x2 matrices. Il s’ensuit également que le produit de A et B est une matrice 4x4, comme prévu. Pour vérifier rapidement l’algorithme, calculer la valeur de l’élément dans la première rangée, première colonne dans le produit. Dans l’exemple, ce serait la valeur de l’élément `ae + bg`dans la première rangée et la première colonne de . Vous n’avez qu’à calculer `ae` la `bg` première colonne, la première rangée de et pour chaque terme. Cette valeur `ae` `(1 * 1) + (2 * 5) = 11`pour est . La valeur de `bg` est `(3 * 1) + (4 * 5) = 23`. La valeur `11 + 23 = 34`finale est , ce qui est correct.

Pour implémenter cet algorithme, le code :

- Utilise `tiled_extent` un objet `extent` au lieu `parallel_for_each` d’un objet dans l’appel.

- Utilise `tiled_index` un objet `index` au lieu `parallel_for_each` d’un objet dans l’appel.

- Crée `tile_static` des variables pour tenir les sous-millions.

- Utilise `tile_barrier::wait` la méthode pour arrêter les fils pour le calcul des produits des sous-millions.

### <a name="to-multiply-by-using-amp-and-tiling"></a>Pour multiplier en utilisant l’AMP et le carrelage

1. Dans MatrixMultiply.cpp, ajoutez le `main` code suivant avant la méthode.

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

   Cet exemple est sensiblement différent de l’exemple sans carrelage. Le code utilise ces étapes conceptuelles :
   1. Copiez les éléments de la tuile[0,0] de `a` dans `locA`. Copiez les éléments de la tuile[0,0] de `b` dans `locB`. Avis `product` qui est carrelé, pas `a` et `b`. Par conséquent, vous utilisez `a, b`des `product`indices globaux pour accéder , et . L’appel `tile_barrier::wait` est essentiel. Il arrête tous les fils dans la `locA` `locB` tuile jusqu’à ce que les deux et sont remplis.

   1. `locA` Multipliez `locB` et mettez `product`les résultats en .

   1. Copiez les éléments de la tuile[0,1] de `a` dans `locA`. Copiez les éléments de tuile [1,0] de `b` dans `locB`.

   1. `locA` Multipliez `locB` et ajoutez-les aux résultats `product`qui sont déjà en .

   1. La multiplication de la tuile[0,0] est complète.

   1. Répétez l’opération pour les quatre autres tuiles. Il n’y a pas d’indexation spécifiquement pour les tuiles et les threads peuvent exécuter dans n’importe quel ordre. Au fur et à `tile_static` mesure que chaque thread s’exécute, `tile_barrier::wait` les variables sont créées pour chaque tuile de manière appropriée et l’appel pour contrôler le flux du programme.

   1. Lorsque vous examinez l’algorithme de près, notez que chaque sousmatrix est chargé dans une `tile_static` mémoire deux fois. Ce transfert de données prend du temps. Cependant, une fois `tile_static` que les données sont en mémoire, l’accès aux données est beaucoup plus rapide. Parce que le calcul des produits nécessite un accès répété aux valeurs dans les sous-millions, il y a un gain de performance global. Pour chaque algorithme, l’expérimentation est nécessaire pour trouver l’algorithme optimal et la taille de la tuile.

   Dans les exemples non-AMP et non-tuile, chaque élément de A et B est accessible quatre fois de la mémoire globale pour calculer le produit. Dans l’exemple de la tuile, chaque élément est accessible `tile_static` deux fois à partir de la mémoire globale et quatre fois de la mémoire. Ce n’est pas un gain de rendement important. Toutefois, si les A et B étaient 1024x1024 matrices et la taille de la tuile étaient 16, il y aurait un gain de performance important. Dans ce cas, chaque élément `tile_static` ne serait copié en mémoire `tile_static` que 16 fois et accessible à partir de la mémoire 1024 fois.

1. Modifier la méthode principale `MultiplyWithTiling` pour appeler la méthode, comme indiqué.

   ```cpp
   int main() {
       MultiplyWithOutAMP();
       MultiplyWithAMP();
       MultiplyWithTiling();
       getchar();
   }
   ```

1. Appuyez sur le raccourci **clavier Ctrl**+**F5** pour commencer à débogage et vérifier que la sortie est correcte.

1. Appuyez sur la barre **Space** pour sortir de l’application.

## <a name="see-also"></a>Voir aussi

[C++ AMP (C++ Accelerated Massive Parallelism)](../../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md)<br/>
[Procédure pas-à-pas : débogage d’une application C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)
