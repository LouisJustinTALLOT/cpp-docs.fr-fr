---
title: 'Procédure : Utiliser Alloc et Free pour améliorer les performances de la mémoire'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: f55bf360ac2b4c7162c1ed2b917ac6ce8c7cd11f
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296122"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Procédure : Utiliser Alloc et Free pour améliorer les performances de la mémoire

Ce document montre comment utiliser le [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) et [concurrency::Free](reference/concurrency-namespace-functions.md#free) fonctions pour améliorer les performances de la mémoire. Il compare la durée requise pour inverser les éléments d’un tableau en parallèle pour trois types différents qui spécifient chacun le `new` et `delete` opérateurs.

Le `Alloc` et `Free` fonctions sont particulièrement utiles lorsque plusieurs threads appellent fréquemment `Alloc` et `Free`. Le runtime maintient un cache mémoire séparé pour chaque thread ; Par conséquent, le runtime gère la mémoire sans utiliser de verrous ou de barrières de mémoire.

## <a name="example"></a>Exemple

L’exemple suivant montre trois types qui spécifient chacun le `new` et `delete` opérateurs. Le `new_delete` classe utilise global `new` et `delete` opérateurs, les `malloc_free` classe utilise le Runtime C [malloc](../../c-runtime-library/reference/malloc.md) et [gratuit](../../c-runtime-library/reference/free.md) fonctions et le `Alloc_Free` classe utilise le Runtime d’accès concurrentiel `Alloc` et `Free` fonctions.

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>Exemple

L'exemple suivant illustre les fonctions `swap` et `reverse_array`. Le `swap` fonction échange le contenu du tableau à l’index spécifiés. Il alloue la mémoire du tas pour la variable temporaire. Le `reverse_array` fonction crée un grand tableau et calcule la durée requise pour inverser ce tableau plusieurs fois en parallèle.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant montre le `wmain` (fonction), qui calcule la durée requise pour le `reverse_array` (fonction) pour agir sur le `new_delete`, `malloc_free`, et `Alloc_Free` types, chacun d’eux utilise une méthode d’allocation de mémoire différentes.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>Exemple

L’exemple complet suit.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Cet exemple produit la sortie suivante pour un ordinateur doté de quatre processeurs.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

Dans cet exemple, le type qui utilise le `Alloc` et `Free` fonctions fournit les meilleures performances de mémoire, car le `Alloc` et `Free` fonctions sont optimisées pour l’allocation et la libération des blocs de mémoire à partir de plusieurs fréquentes threads.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `allocators.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc allocators.cpp**

## <a name="see-also"></a>Voir aussi

[Fonctions de gestion de la mémoire](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc, fonction](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free (fonction)](reference/concurrency-namespace-functions.md#free)
