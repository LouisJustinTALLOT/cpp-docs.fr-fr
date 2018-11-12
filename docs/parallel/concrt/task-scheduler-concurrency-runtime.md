---
title: Planificateur de tâches (runtime d’accès concurrentiel)
ms.date: 11/04/2016
helpviewer_keywords:
- oversubscription [Concurrency Runtime]
- task scheduler [Concurrency Runtime], oversubscription
- schedule groups [Concurrency Runtime]
- task scheduler [Concurrency Runtime], lightweight tasks
- task scheduler [Concurrency Runtime]
- lightweight tasks [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler policies
- task scheduler [Concurrency Runtime], schedule groups
- wait function [Concurrency Runtime]
- task scheduler [Concurrency Runtime], scheduler instances
- scheduler instances [Concurrency Runtime]
- scheduler policies [Concurrency Runtime]
- task scheduler [Concurrency Runtime], wait function
ms.assetid: 9aba278c-e0c9-4ede-b7c6-fedf7a365d90
ms.openlocfilehash: 91ef4ed14fa1ddc25ff494f6666a50f5b39b8a54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50676705"
---
# <a name="task-scheduler-concurrency-runtime"></a>Planificateur de tâches (runtime d’accès concurrentiel)

Les rubriques de cette partie de la documentation décrivent les fonctionnalités importantes du planificateur de tâches du runtime d’accès concurrentiel. Le planificateur de tâches s’avère utile quand vous voulez affiner les performances de votre code existant qui utilise le runtime d’accès concurrentiel.

> [!IMPORTANT]
>  Le Planificateur de tâches n’est pas disponible à partir d’une application de plateforme universelle Windows (UWP). Pour plus d’informations, consultez [création d’opérations asynchrones en C++ pour les applications UWP](../../parallel/concrt/creating-asynchronous-operations-in-cpp-for-windows-store-apps.md).
>
>  Dans Visual Studio 2015 et versions ultérieures, le [concurrency::task](../../parallel/concrt/reference/task-class.md) classe et des types associés dans ppltasks.h utilisent le pool de threads Windows comme planificateur. Cette rubrique ne s'applique plus aux types qui sont définis dans ppltasks.h. Les algorithmes parallèles comme parallel_for continuent à utiliser le runtime d'accès concurrentiel en tant que planificateur par défaut.

> [!TIP]
>  Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à optimiser les performances de vos applications, nous vous recommandons de commencer avec le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous êtes nouvelle pour le Runtime d’accès concurrentiel.

Le planificateur de tâches planifie et coordonne les tâches au moment de l’exécution. Un *tâche* est une unité de travail qui exécute un travail spécifique. En règle générale, une tâche peut s’exécuter en parallèle avec d’autres tâches. Le travail effectué par les éléments de groupe de tâches, les algorithmes parallèles et les agents asynchrones sont tous des exemples de tâches.

Le planificateur de tâches gère les détails liés à la planification efficace des tâches sur les ordinateurs dotés de multiples ressources informatiques. Il utilise également les nouvelles fonctionnalités du système d'exploitation sous-jacent. Par conséquent, les applications qui utilisent le runtime d’accès concurrentiel évoluent et s’améliorent automatiquement sur du matériel qui possède des capacités développées.

[Comparaison aux autres modèles d’accès concurrentiel](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md) décrit les différences entre les mécanismes de planification préemptifs et coopératives. Le planificateur de tâches utilise la planification coopérative et un algorithme de vol de travail avec le planificateur de préemption du système d’exploitation pour optimiser l’utilisation des ressources de traitement.

Le runtime d'accès concurrentiel fournit un planificateur par défaut pour vous éviter d'avoir à gérer les détails de l'infrastructure. Ainsi, vous n'utilisez habituellement pas le planificateur de tâches directement. Toutefois, pour répondre aux besoins de qualité de votre application, vous pouvez utiliser le planificateur de tâches pour fournir votre propre stratégie de planification ou associer des planificateurs spécifiques à des tâches spécifiques. Par exemple, supposons que vous ayez une routine de tri parallèle qui n'évolue pas au-delà de quatre processeurs. Vous pouvez utiliser *des stratégies de planificateur* pour créer un planificateur qui ne génère pas plus de quatre tâches simultanées. L'exécution de la routine de tri sur ce planificateur permet aux autres planificateurs actifs d'utiliser toutes les ressources de traitement restantes.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Instances de planificateur](../../parallel/concrt/scheduler-instances.md)|Décrit les instances de planificateur et la manière d'utiliser les classes `concurrency::Scheduler` et `concurrency::CurrentScheduler` pour les gérer. Utilisez les instances de planificateur pour associer des stratégies de planification explicites à des types spécifiques de charges de travail.|
|[Stratégies de planificateur](../../parallel/concrt/scheduler-policies.md)|Décrit le rôle des stratégies de planificateur. Utilisez des stratégies de planificateur pour contrôler la stratégie utilisée par le planificateur pour gérer des tâches.|
|[Groupes de planification](../../parallel/concrt/schedule-groups.md)|Décrit le rôle des groupes de planification. Utilisez des groupes de planification quand vous avez besoin d’un degré élevé de localité entre les tâches, par exemple, quand un groupe de tâches connexes tire parti d’une exécution sur le même nœud de processeur.|
|[Tâches légères](../../parallel/concrt/lightweight-tasks.md)|Décrit le rôle des tâches légères. Les tâches légères s’avèrent utiles quand vous adaptez du code existant pour utiliser les fonctionnalités de planification du runtime d’accès concurrentiel.|
|[Contextes](../../parallel/concrt/contexts.md)|Décrit le rôle des contextes, la fonction `concurrency::wait` et la classe `concurrency::Context`. Utilisez cette fonctionnalité quand vous avez besoin de contrôler le moment auquel les contextes bloquent, débloquent et produisent, ou quand vous voulez activer le surabonnement dans votre application.|
|[Fonctions de gestion de la mémoire](../../parallel/concrt/memory-management-functions.md)|Décrit les fonctions `concurrency::Alloc` et `concurrency::Free`. Ces fonctions peuvent améliorer les performances de la mémoire en allouant ou en libérant de la mémoire de façon simultanée.|
|[Comparaison aux autres modèles d’accès concurrentiel](../../parallel/concrt/comparing-the-concurrency-runtime-to-other-concurrency-models.md)|Décrit les différences entre les mécanismes de planification de préemption et de coopération.|
|[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)|Décrit comment utiliser divers modèles parallèles, par exemple, des algorithmes parallèles, dans vos applications.|
|[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)|Décrit comment utiliser des agents asynchrones dans vos applications.|
|[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)|Décrit le runtime d'accès concurrentiel, qui simplifie la programmation parallèle, et contient des liens vers les rubriques connexes.|

