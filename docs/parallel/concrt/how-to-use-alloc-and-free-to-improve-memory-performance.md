---
title: 'Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: 8438e833262d42c6083f48f759501c573a35c772
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142788"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire

Ce document montre comment utiliser les fonctions [Concurrency :: Alloc](reference/concurrency-namespace-functions.md#alloc) et [Concurrency :: Free](reference/concurrency-namespace-functions.md#free) pour améliorer les performances de la mémoire. Il compare le temps nécessaire pour inverser les éléments d’un tableau en parallèle pour trois types différents qui spécifient chacun les opérateurs `new` et `delete`.

Les fonctions `Alloc` et `Free` sont particulièrement utiles lorsque plusieurs threads appellent fréquemment des `Alloc` et des `Free`. Le runtime conserve un cache mémoire distinct pour chaque thread. par conséquent, le Runtime gère la mémoire sans l’utilisation de verrous ou de barrières de mémoire.

## <a name="example"></a>Exemple

L’exemple suivant montre trois types qui spécifient chacun les opérateurs `new` et `delete`. La classe `new_delete` utilise les opérateurs globaux `new` et `delete`, la classe `malloc_free` utilise les fonctions [malloc](../../c-runtime-library/reference/malloc.md) et [Free](../../c-runtime-library/reference/free.md) du runtime C, et la classe `Alloc_Free` utilise les fonctions runtime d’accès concurrentiel `Alloc` et `Free`.

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example"></a>Exemple

L'exemple suivant illustre les fonctions `swap` et `reverse_array`. La fonction `swap` échange le contenu du tableau aux index spécifiés. Elle alloue de la mémoire à partir du tas pour la variable temporaire. La fonction `reverse_array` crée un grand tableau et calcule le temps nécessaire pour inverser ce tableau plusieurs fois en parallèle.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant illustre la fonction `wmain`, qui calcule le temps nécessaire à la fonction `reverse_array` pour agir sur les types `new_delete`, `malloc_free`et `Alloc_Free`, chacun d’entre eux utilisant un schéma d’allocation de mémoire différent.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="example"></a>Exemple

L’exemple complet suit.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Cet exemple produit l’exemple de sortie suivant pour un ordinateur doté de quatre processeurs.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

Dans cet exemple, le type qui utilise les fonctions `Alloc` et `Free` fournit les meilleures performances de mémoire, car les fonctions `Alloc` et `Free` sont optimisées pour l’allocation et la libération fréquentes de blocs de mémoire à partir de plusieurs threads.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `allocators.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc allocators. cpp**

## <a name="see-also"></a>Voir aussi

[Fonctions de gestion de la mémoire](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc, fonction](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free, fonction](reference/concurrency-namespace-functions.md#free)
