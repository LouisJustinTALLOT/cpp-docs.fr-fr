---
description: 'En savoir plus sur : Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire'
title: 'Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire'
ms.date: 11/04/2016
helpviewer_keywords:
- Alloc and Free, using [Concurrency Runtime]
- Using Alloc and Free [Concurrency Runtime]
ms.assetid: e1fab9e8-a97d-4104-bead-e95958db79f9
ms.openlocfilehash: ab9a7bb9ad067bd7a5650b9e66d1708f08ffc183
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172568"
---
# <a name="how-to-use-alloc-and-free-to-improve-memory-performance"></a>Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire

Ce document montre comment utiliser les fonctions [Concurrency :: Alloc](reference/concurrency-namespace-functions.md#alloc) et [Concurrency :: Free](reference/concurrency-namespace-functions.md#free) pour améliorer les performances de la mémoire. Il compare le temps nécessaire pour inverser les éléments d’un tableau en parallèle pour trois types différents qui spécifient chacun `new` les `delete` opérateurs et.

Les `Alloc` `Free` fonctions et sont particulièrement utiles lorsque plusieurs threads appellent fréquemment `Alloc` et `Free` . Le runtime conserve un cache mémoire distinct pour chaque thread. par conséquent, le Runtime gère la mémoire sans l’utilisation de verrous ou de barrières de mémoire.

## <a name="example-types-that-specify-new-and-delete-operators"></a>Exemple : types qui spécifient des opérateurs New et Delete

L’exemple suivant montre trois types qui spécifient chacun `new` les `delete` opérateurs et. La `new_delete` classe utilise les opérateurs globaux `new` et `delete` , la `malloc_free` classe utilise les fonctions [malloc](../../c-runtime-library/reference/malloc.md) et [Free](../../c-runtime-library/reference/free.md) du runtime C, et la `Alloc_Free` classe utilise les `Alloc` fonctions runtime d’accès concurrentiel et `Free` .

[!code-cpp[concrt-allocators#1](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_1.cpp)]

## <a name="example-swap-and-reverse_array-functions"></a>Exemple : fonctions swap et reverse_array

L'exemple suivant illustre les fonctions `swap` et `reverse_array`. La `swap` fonction échange le contenu du tableau aux index spécifiés. Elle alloue de la mémoire à partir du tas pour la variable temporaire. La `reverse_array` fonction crée un grand tableau et calcule le temps nécessaire pour inverser ce tableau plusieurs fois en parallèle.

[!code-cpp[concrt-allocators#2](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_2.cpp)]

## <a name="example-wmain-function"></a>Exemple : fonction wmain

L’exemple suivant illustre la `wmain` fonction, qui calcule le temps nécessaire pour que la `reverse_array` fonction agisse sur les `new_delete` `malloc_free` types, et, dont `Alloc_Free` chacun utilise un schéma d’allocation de mémoire différent.

[!code-cpp[concrt-allocators#3](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_3.cpp)]

## <a name="complete-code-example"></a>Exemple de code complet

L’exemple complet suit.

[!code-cpp[concrt-allocators#4](../../parallel/concrt/codesnippet/cpp/how-to-use-alloc-and-free-to-improve-memory-performance_4.cpp)]

Cet exemple produit l’exemple de sortie suivant pour un ordinateur doté de quatre processeurs.

```Output
Took 2031 ms with new/delete.
Took 1672 ms with malloc/free.
Took 656 ms with Alloc/Free.
```

Dans cet exemple, le type qui utilise les `Alloc` `Free` fonctions et fournit les meilleures performances de mémoire, car les `Alloc` `Free` fonctions et sont optimisées pour l’allocation et la libération fréquentes de blocs de mémoire à partir de plusieurs threads.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `allocators.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc allocators. cpp**

## <a name="see-also"></a>Voir aussi

[Fonctions de gestion de la mémoire](../../parallel/concrt/memory-management-functions.md)<br/>
[Alloc, fonction](reference/concurrency-namespace-functions.md#alloc)<br/>
[Free, fonction](reference/concurrency-namespace-functions.md#free)
