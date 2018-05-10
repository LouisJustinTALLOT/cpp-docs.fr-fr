---
title: Les fonctions de gestion de mémoire | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- memory management functions [Concurrency Runtime]
ms.assetid: d303dd2a-dfa4-4d90-a508-f6aa290bb9ea
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f0a298c7fb9e50bb17d37224b69ce342c54115d7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
---
# <a name="memory-management-functions"></a>Fonctions de gestion de la mémoire
Ce document décrit les fonctions de gestion de mémoire que le Runtime d’accès concurrentiel fournit pour vous aider à allouer et libérer de la mémoire de façon simultanée.  
  
> [!TIP]
>  Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à optimiser les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous êtes nouveau pour le Runtime d’accès concurrentiel.  
  
 Le Runtime d’accès concurrentiel fournit deux fonctions de gestion de mémoire qui sont optimisées pour l’allocation et la libération des blocs de mémoire de façon simultanée. Le [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) fonction alloue un bloc de mémoire à l’aide de la taille spécifiée. Le [concurrency::Free](reference/concurrency-namespace-functions.md#free) fonction libère la mémoire allouée par `Alloc`.  
  
> [!NOTE]
>  Le `Alloc` et `Free` fonctions s’appuient sur eux. Utilisez le `Free` fonction uniquement pour libérer la mémoire que vous allouez à l’aide de la `Alloc` (fonction). En outre, lorsque vous utilisez la `Alloc` fonction pour allouer de la mémoire, utilisez uniquement le `Free` afin de libérer cette mémoire.  
  
 Utilisez le `Alloc` et `Free` fonctions lorsque vous allouez et libérez un jeu fixe de tailles d’allocation de threads ou tâches différents. Le Runtime d’accès concurrentiel met en cache mémoire qu’il alloue à partir du tas Runtime C. Le Runtime d’accès concurrentiel maintient un cache mémoire séparé pour chaque thread en cours d’exécution ; Par conséquent, le runtime gère la mémoire sans utiliser de verrous ou de barrières de mémoire. Une application bénéficie d’informations à partir de la `Alloc` et `Free` fonctionne lorsque le cache mémoire sont plus sollicitées. Par exemple, un thread qui appelle fréquemment `Alloc` et `Free` avantages plus qu’un thread qui appelle principalement `Alloc` ou `Free`.  
  
> [!NOTE]
>  Lorsque vous utilisez ces fonctions de gestion de mémoire, et que votre application utilise beaucoup de mémoire, l’application peut entrer une condition de mémoire faible plus tôt que vous attendez. Étant donné que les blocs de mémoire qui sont mis en cache par un thread ne sont pas disponibles pour aucun autre thread, si un thread détient une grande quantité de mémoire, cette mémoire n’est pas disponible.  
  
## <a name="example"></a>Exemple  
 Pour obtenir un exemple qui utilise le `Alloc` et `Free` fonctions afin d’améliorer les performances de la mémoire, consultez [Comment : utiliser Alloc et Free pour améliorer les performances de mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Guide pratique pour utiliser Alloc et Free pour améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)

