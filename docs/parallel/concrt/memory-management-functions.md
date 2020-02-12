---
title: Fonctions de gestion de la mémoire
ms.date: 11/04/2016
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
ms.openlocfilehash: aa1951211283ddf7e4823a920d5cdf19bd6d977d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141843"
---
# <a name="memory-management-functions"></a>Fonctions de gestion de la mémoire

Ce document décrit les fonctions de gestion de la mémoire fournies par le runtime d’accès concurrentiel pour vous aider à allouer et libérer de la mémoire de façon simultanée.

> [!TIP]
> Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à ajuster les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous débutez avec le runtime d’accès concurrentiel.

L’runtime d’accès concurrentiel fournit deux fonctions de gestion de la mémoire qui sont optimisées pour allouer et libérer des blocs de mémoire de façon simultanée. La fonction [Concurrency :: Alloc](reference/concurrency-namespace-functions.md#alloc) alloue un bloc de mémoire à l’aide de la taille spécifiée. La fonction [Concurrency :: Free](reference/concurrency-namespace-functions.md#free) libère la mémoire qui a été allouée par `Alloc`.

> [!NOTE]
> Les fonctions `Alloc` et `Free` s’appuient les unes sur les autres. Utilisez la fonction `Free` uniquement pour libérer de la mémoire que vous allouez à l’aide de la fonction `Alloc`. En outre, lorsque vous utilisez la fonction `Alloc` pour allouer de la mémoire, utilisez uniquement la fonction `Free` pour libérer cette mémoire.

Utilisez les fonctions `Alloc` et `Free` quand vous allouez et libérez un ensemble fixe de tailles d’allocation à partir de threads ou de tâches différents. Le runtime d’accès concurrentiel met en cache la mémoire qu’il alloue à partir du tas du runtime C. Le runtime d’accès concurrentiel détient un cache mémoire distinct pour chaque thread en cours d’exécution ; par conséquent, le Runtime gère la mémoire sans l’utilisation de verrous ou de barrières de mémoire. Une application tire davantage parti des fonctions `Alloc` et `Free` lorsque le cache mémoire fait l’accès plus fréquemment. Par exemple, un thread qui appelle fréquemment `Alloc` et `Free` avantages plus qu’un thread qui appelle principalement `Alloc` ou `Free`.

> [!NOTE]
> Lorsque vous utilisez ces fonctions de gestion de la mémoire et que votre application utilise une grande quantité de mémoire, l’application peut entrer une condition de mémoire insuffisante plus tôt que prévu. Étant donné que les blocs de mémoire qui sont mis en cache par un thread ne sont pas disponibles pour un autre thread, si un thread détient beaucoup de mémoire, cette mémoire n’est pas disponible.

## <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise les fonctions `Alloc` et `Free` pour améliorer les performances de la mémoire, consultez [Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Guide pratique pour utiliser Alloc et Free pour améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)
