---
description: 'En savoir plus sur : meilleures pratiques générales dans le runtime d’accès concurrentiel'
title: Meilleures pratiques en général du runtime d’accès concurrentiel
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: a0de8d9a0070bfc0691aeb9484c755cbfcbb40b1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97197424"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Meilleures pratiques en général du runtime d’accès concurrentiel

Ce document décrit les meilleures pratiques qui s’appliquent à plusieurs zones du runtime d’accès concurrentiel.

## <a name="sections"></a><a name="top"></a> Sections

Ce document contient les sections suivantes :

- [Utiliser les constructions de synchronisation coopérative lorsque cela est possible](#synchronization)

- [Évitez les tâches longues qui ne génèrent pas](#yield)

- [Utiliser le surabonnement pour décaler les opérations qui bloquent ou ont une latence élevée](#oversubscription)

- [Utilisez des fonctions de gestion simultanée de la mémoire lorsque cela est possible](#memory)

- [Utiliser RAII pour gérer la durée de vie des objets de concurrence](#raii)

- [Ne pas créer d’objets de concurrence au niveau de la portée globale](#global-scope)

- [Ne pas utiliser d’objets d’accès concurrentiel dans des segments de données partagés](#shared-data)

## <a name="use-cooperative-synchronization-constructs-when-possible"></a><a name="synchronization"></a> Utiliser les constructions de synchronisation coopérative lorsque cela est possible

Le runtime d’accès concurrentiel fournit de nombreuses constructions de concurrence sécurisée qui ne nécessitent pas d’objet de synchronisation externe. Par exemple, la classe [Concurrency :: concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) fournit des opérations d’ajout et d’accès à l’élément sécurisées pour l’accès concurrentiel. Ici, l’accès concurrentiel sécurisé signifie que les pointeurs ou les itérateurs sont toujours valides. Il ne s’agit pas d’une garantie d’initialisation d’élément ou d’un ordre de parcours particulier. Toutefois, dans les cas où vous avez besoin d’un accès exclusif à une ressource, le Runtime fournit les classes [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md), [Concurrency :: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md)et [Concurrency :: Event](../../parallel/concrt/reference/event-class.md) . Ces types se comportent de manière coopérative ; par conséquent, le planificateur de tâches peut réallouer les ressources de traitement à un autre contexte lorsque la première tâche attend des données. Dans la mesure du possible, utilisez ces types de synchronisation au lieu d’autres mécanismes de synchronisation, tels que ceux fournis par l’API Windows, qui ne se comportent pas de manière coopérative. Pour plus d’informations sur ces types de synchronisation et un exemple de code, consultez [structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md) et comparaison des [structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Haut](#top)]

## <a name="avoid-lengthy-tasks-that-do-not-yield"></a><a name="yield"></a> Évitez les tâches longues qui ne génèrent pas

Étant donné que le planificateur de tâches se comporte de manière coopérative, il ne fournit pas d’équité entre les tâches. Par conséquent, une tâche peut empêcher le démarrage d’autres tâches. Bien que cela soit acceptable dans certains cas, cela peut entraîner un blocage ou une privation.

L’exemple suivant effectue plus de tâches que le nombre de ressources de traitement allouées. La première tâche ne génère pas le planificateur de tâches et par conséquent, la deuxième tâche ne démarre pas tant que la première tâche n’est pas terminée.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

Cet exemple produit la sortie suivante :

1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Il existe plusieurs façons d’activer la coopération entre les deux tâches. L’une des méthodes consiste à générer occasionnellement le planificateur de tâches dans une tâche de longue durée. L’exemple suivant modifie la `task` fonction pour appeler la méthode [Concurrency :: Context :: Yield](reference/context-class.md#yield) pour permettre l’exécution au planificateur de tâches afin qu’une autre tâche puisse s’exécuter.

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

Cet exemple produit la sortie suivante :

```Output
1: 250000000
2: 250000000
1: 500000000
2: 500000000
1: 750000000
2: 750000000
1: 1000000000
2: 1000000000
```

La `Context::Yield` méthode ne produit qu’un autre thread actif sur le planificateur auquel appartient le thread actuel, une tâche légère ou un autre thread de système d’exploitation. Cette méthode ne génère pas de travail planifié pour s’exécuter dans un objet [Concurrency :: task_group](reference/task-group-class.md) ou [Concurrency :: structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) , mais n’a pas encore démarré.

Il existe d’autres moyens d’activer la coopération entre les tâches de longue durée. Vous pouvez diviser une tâche volumineuse en tâches subordonnées plus petites. Vous pouvez également activer le surabonnement pendant une tâche de longue durée. Le surabonnement vous permet de créer un nombre de threads plus important que le nombre de threads matériels disponibles. Le surabonnement est particulièrement utile lorsqu’une tâche de longue durée contient une latence élevée, par exemple la lecture de données à partir d’un disque ou d’une connexion réseau. Pour plus d’informations sur les tâches légères et le surabonnement, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Haut](#top)]

## <a name="use-oversubscription-to-offset-operations-that-block-or-have-high-latency"></a><a name="oversubscription"></a> Utiliser le surabonnement pour décaler les opérations qui bloquent ou ont une latence élevée

Le runtime d’accès concurrentiel fournit des primitives de synchronisation, telles que [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md), qui permettent aux tâches de se bloquer et de se céder les unes aux autres. Lorsqu’une tâche se bloque ou cède de façon coopérative, le planificateur de tâches peut réallouer les ressources de traitement à un autre contexte lorsque la première tâche attend des données.

Dans certains cas, vous ne pouvez pas utiliser le mécanisme de blocage coopératif fourni par le runtime d’accès concurrentiel. Par exemple, une bibliothèque externe que vous utilisez peut utiliser un mécanisme de synchronisation différent. Un autre exemple est lorsque vous effectuez une opération qui peut avoir une latence élevée, par exemple, lorsque vous utilisez la fonction d’API Windows `ReadFile` pour lire des données à partir d’une connexion réseau. Dans ce cas, le surabonnement peut permettre à d’autres tâches de s’exécuter lorsqu’une autre tâche est inactive. Le surabonnement vous permet de créer un nombre de threads plus important que le nombre de threads matériels disponibles.

Considérez la fonction suivante, `download` , qui télécharge le fichier à l’URL donnée. Cet exemple utilise la méthode [Concurrency :: Context :: Oversubscribe](reference/context-class.md#oversubscribe) pour augmenter temporairement le nombre de threads actifs.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Étant donné que la `GetHttpFile` fonction effectue une opération potentiellement latente, le surabonnement peut permettre à d’autres tâches de s’exécuter au fur et à mesure que la tâche actuelle attend des données. Pour obtenir la version complète de cet exemple, consultez [Comment : utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Haut](#top)]

## <a name="use-concurrent-memory-management-functions-when-possible"></a><a name="memory"></a> Utilisez des fonctions de gestion simultanée de la mémoire lorsque cela est possible

Utilisez les fonctions de gestion de la mémoire, la [concurrence :: Alloc](reference/concurrency-namespace-functions.md#alloc) et l' [accès concurrentiel :: Free](reference/concurrency-namespace-functions.md#free), lorsque vous avez des tâches affinées qui allouez fréquemment de petits objets qui ont une durée de vie relativement courte. Le runtime d’accès concurrentiel détient un cache mémoire distinct pour chaque thread en cours d’exécution. Les `Alloc` `Free` fonctions et allouent et libèrent de la mémoire à partir de ces caches sans l’utilisation de verrous ou de barrières de mémoire.

Pour plus d’informations sur ces fonctions de gestion de la mémoire, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Pour obtenir un exemple qui utilise ces fonctions, consultez [Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

[[Haut](#top)]

## <a name="use-raii-to-manage-the-lifetime-of-concurrency-objects"></a><a name="raii"></a> Utiliser RAII pour gérer la durée de vie des objets de concurrence

Le runtime d’accès concurrentiel utilise la gestion des exceptions pour implémenter des fonctionnalités telles que l’annulation. Par conséquent, écrivez du code sécurisé au moment de l’exception quand vous appelez le runtime ou appelez une autre bibliothèque qui appelle le Runtime.

Le modèle RAII ( *Resource Acquisition Is Initialization* ) est un moyen de gérer en toute sécurité la durée de vie d’un objet d’accès concurrentiel dans une étendue donnée. Dans le modèle RAII, une structure de données est allouée sur la pile. Cette structure de données Initialise ou acquiert une ressource lors de sa création et détruit ou libère cette ressource lorsque la structure de données est détruite. Le modèle RAII garantit que le destructeur est appelé avant la sortie de la portée englobante. Ce modèle est utile lorsqu’une fonction contient plusieurs **`return`** instructions. Ce modèle vous aide également à écrire du code sécurisé contre les exceptions. Lorsqu’une **`throw`** instruction provoque le déroulement de la pile, le destructeur de l’objet RAII est appelé ; par conséquent, la ressource est toujours correctement supprimée ou libérée.

Le runtime définit plusieurs classes qui utilisent le modèle RAII, par exemple, [Concurrency :: critical_section :: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) et [Concurrency :: reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Ces classes d’assistance sont appelées *verrous étendus*. Ces classes offrent plusieurs avantages quand vous travaillez avec des objets [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md) ou [Concurrency :: reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) . Le constructeur de ces classes acquiert l’accès à l' `critical_section` objet ou fourni `reader_writer_lock` ; le destructeur libère l’accès à cet objet. Étant donné qu’un verrou étendu libère automatiquement l’accès à son objet d’exclusion mutuelle lorsqu’il est détruit, vous ne Déverrouillez pas manuellement l’objet sous-jacent.

Considérons la classe suivante, `account` , qui est définie par une bibliothèque externe et qui, par conséquent, ne peut pas être modifiée.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

L’exemple suivant effectue plusieurs transactions sur un `account` objet en parallèle. L’exemple utilise un `critical_section` objet pour synchroniser l’accès à l' `account` objet, car la `account` classe n’est pas sécurisée pour la concurrence. Chaque opération parallèle utilise un `critical_section::scoped_lock` objet pour garantir que l' `critical_section` objet est déverrouillé lorsque l’opération réussit ou échoue. Lorsque le solde du compte est négatif, l' `withdraw` opération échoue en levant une exception.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

Cet exemple produit l’exemple de sortie suivant :

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

Pour obtenir des exemples supplémentaires qui utilisent le modèle RAII pour gérer la durée de vie des objets de concurrence, consultez [procédure pas à pas : suppression de travail d’un thread de User-Interface](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [Comment : utiliser la classe de contexte pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)et [Comment : utiliser le surabonnement pour décaler la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Haut](#top)]

## <a name="do-not-create-concurrency-objects-at-global-scope"></a><a name="global-scope"></a> Ne pas créer d’objets de concurrence au niveau de la portée globale

Lorsque vous créez un objet d’accès concurrentiel au niveau de la portée globale, vous pouvez provoquer des problèmes tels que des violations d’accès mémoire ou des interblocages dans votre application.

Par exemple, lorsque vous créez un objet runtime d’accès concurrentiel, le runtime crée un planificateur par défaut si aucun n’a été créé. Un objet d’exécution créé pendant la construction d’un objet global entraînera en conséquence que le runtime crée ce planificateur par défaut. Toutefois, ce processus prend un verrou interne, qui peut interférer avec l’initialisation d’autres objets qui prennent en charge l’infrastructure runtime d’accès concurrentiel. Ce verrou interne peut être requis par un autre objet d’infrastructure qui n’a pas encore été initialisé et peut donc entraîner un interblocage dans votre application.

L’exemple suivant illustre la création d’un objet global [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) . Ce modèle s’applique non seulement à la `Scheduler` classe, mais aussi à tous les autres types fournis par le runtime d’accès concurrentiel. Nous vous recommandons de ne pas suivre ce modèle, car cela peut provoquer un comportement inattendu dans votre application.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Pour obtenir des exemples de la façon correcte de créer des `Scheduler` objets, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Haut](#top)]

## <a name="do-not-use-concurrency-objects-in-shared-data-segments"></a><a name="shared-data"></a> Ne pas utiliser d’objets d’accès concurrentiel dans des segments de données partagés

La runtime d’accès concurrentiel ne prend pas en charge l’utilisation d’objets concurrentiels dans une section de données partagées, par exemple, une section de données créée par la directive [data_seg](../../preprocessor/data-seg.md) `#pragma` . Un objet d’accès concurrentiel partagé entre des limites de processus peut mettre le runtime dans un état incohérent ou non valide.

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques en matière de runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Comparaison des structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[Comment : utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[Comment : utiliser la classe Context pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Procédure pas à pas : suppression de travail d’un thread de User-Interface](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[Meilleures pratiques dans la bibliothèque de modèles parallèles](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Meilleures pratiques dans la bibliothèque des agents asynchrones](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
