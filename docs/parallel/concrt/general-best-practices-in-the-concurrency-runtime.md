---
title: Meilleures pratiques en général du runtime d’accès concurrentiel
ms.date: 11/04/2016
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
ms.openlocfilehash: e25011e2466d76c946cc55421ed228c8ea174161
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62413916"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Meilleures pratiques en général du runtime d’accès concurrentiel

Ce document décrit les meilleures pratiques qui s’appliquent à plusieurs zones du Runtime d’accès concurrentiel.

##  <a name="top"></a> Sections

Ce document contient les sections suivantes :

- [Utiliser des éléments de synchronisation coopérative lorsque cela est Possible](#synchronization)

- [Éviter les tâches longues qui ne génèrent pas](#yield)

- [Utiliser le surabonnement pour compenser les opérations qui bloquent ou présenter une latence élevée](#oversubscription)

- [Utiliser les fonctions de gestion de mémoire simultanées lorsque cela est Possible](#memory)

- [Utiliser RAII pour gérer la durée de vie des objets d’accès concurrentiel](#raii)

- [Ne créez pas d’objets d’accès concurrentiel dans une portée globale](#global-scope)

- [N’utilisez pas les objets d’accès concurrentiel dans les Segments de données partagées](#shared-data)

##  <a name="synchronization"></a> Utiliser des éléments de synchronisation coopérative lorsque cela est Possible

Le Runtime d’accès concurrentiel fournit de nombreuses constructions d’accès concurrentiel sécurisé qui ne nécessitent pas un objet de synchronisation externe. Par exemple, le [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) classe fournit concurrentiel append et élément accéder aux opérations. Toutefois, pour les cas où vous avez besoin d’un accès exclusif à une ressource, le runtime fournit le [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md), et [l’accès concurrentiel :: événement](../../parallel/concrt/reference/event-class.md) classes. Ces types se comportent de manière coopérative ; Par conséquent, le Planificateur de tâches peut réaffecter les ressources de traitement à un autre contexte que la première tâche attend des données. Si possible, utilisez ces types de synchronisation au lieu d’autres mécanismes de synchronisation, telles que celles fournies par l’API Windows, qui ne fonctionnent pas de manière coopérative. Pour plus d’informations sur ces types de synchronisation et un exemple de code, consultez [les Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md) et [comparaison des Structures de données de synchronisation à l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).

[[Haut](#top)]

##  <a name="yield"></a> Éviter les tâches longues qui ne génèrent pas

Étant donné que le Planificateur de tâches se comporte de manière coopérative, il ne fournit pas d’équité parmi les tâches. Par conséquent, une tâche peut empêcher autres tâches de démarrage. Bien que cela est acceptable dans certains cas, dans d’autres cas, cela peut provoquer un blocage ou la privation.

L’exemple suivant effectue des tâches plus que le nombre de ressources de traitement allouées. La première tâche ne génère pas le Planificateur de tâches et par conséquent, la seconde tâche ne démarre pas tant que la première tâche se termine.

[!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]

Cet exemple génère la sortie suivante :

1 : 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000

Il existe plusieurs façons d’activer la coopération entre les deux tâches. La première consiste à céder occasionnellement au planificateur de tâches dans une tâche à long terme. L’exemple suivant modifie le `task` fonction à appeler le [Concurrency::Context :: yield](reference/context-class.md#yield) méthode à céder l’exécution au planificateur de tâches afin qu’une autre tâche peut s’exécuter.

[!code-cpp[concrt-cooperative-tasks#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_2.cpp)]

Cet exemple génère la sortie suivante :

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

Le `Context::Yield` méthode donne uniquement un autre thread actif sur le planificateur auquel le thread actuel appartient, une tâche légère ou un autre thread de système d’exploitation. Cette méthode ne génère pas de travail qui est planifiée pour s’exécuter un [concurrency::task_group](reference/task-group-class.md) ou [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) objet mais n’a pas encore démarré.

Autres manières d’activer la coopération entre les tâches longues. Vous pouvez scinder une grande tâche en sous-tâches plus petites. Vous pouvez également activer le surabonnement pendant une tâche de longue durée. Le surabonnement vous permet de créer un nombre de threads plus important que le nombre de threads matériels disponibles. Le surabonnement est particulièrement utile lorsqu’une tâche longue contient une grande quantité de latence, par exemple, lire des données à partir du disque ou d’une connexion réseau. Pour plus d’informations sur les tâches légères et le surabonnement, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Haut](#top)]

##  <a name="oversubscription"></a> Utiliser le surabonnement pour compenser les opérations qui bloquent ou présenter une latence élevée

Le Runtime d’accès concurrentiel fournit des primitives de synchronisation, tel que [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), qui permettent des tâches de manière coopérative bloquer yield entre eux. Lorsqu’une tâche bloque de manière coopérative ou produit, le Planificateur de tâches peut réaffecter les ressources de traitement à un autre contexte que la première tâche attend des données.

Il existe des cas dans lequel vous ne pouvez pas utiliser le mécanisme de blocage coopératif qui est fourni par le Runtime d’accès concurrentiel. Par exemple, une bibliothèque externe que vous utilisez peut utiliser un mécanisme de synchronisation différents. Un autre exemple est lorsque vous effectuez une opération qui peut présenter une grande quantité de latence, par exemple, lorsque vous utilisez l’API Windows `ReadFile` fonction permettant de lire des données à partir d’une connexion réseau. Dans ce cas, le surabonnement peut permettre d’autres tâches à exécuter quand une autre tâche est inactive. Le surabonnement vous permet de créer un nombre de threads plus important que le nombre de threads matériels disponibles.

Considérez la fonction suivante, `download`, qui télécharge le fichier à l’URL donnée. Cet exemple utilise le [Concurrency::Context :: Oversubscribe](reference/context-class.md#oversubscribe) méthode pour augmenter provisoirement le nombre de threads actifs.

[!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]

Étant donné que le `GetHttpFile` fonction effectue une opération potentiellement latente, le surabonnement peut permettre d’autres tâches à exécuter la tâche en cours attend des données. Pour obtenir la version complète de cet exemple, consultez [Comment : Utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Haut](#top)]

##  <a name="memory"></a> Utiliser les fonctions de gestion de mémoire simultanées lorsque cela est Possible

Utilisez les fonctions de gestion de mémoire, [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) et [concurrency::Free](reference/concurrency-namespace-functions.md#free), lorsque vous avez des tâches affinées qui allouent fréquemment des petits objets qui ont une durée de vie relativement courte. Le Runtime d’accès concurrentiel maintient un cache de mémoire distincts pour chaque thread en cours d’exécution. Le `Alloc` et `Free` fonctions allouent et libèrent la mémoire à partir de ces caches sans utiliser de verrous ou de barrières de mémoire.

Pour plus d’informations sur ces fonctions de gestion de mémoire, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Pour obtenir un exemple qui utilise ces fonctions, consultez [Comment : Utiliser Alloc et Free pour améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).

[[Haut](#top)]

##  <a name="raii"></a> Utiliser RAII pour gérer la durée de vie des objets d’accès concurrentiel

Le Runtime d’accès concurrentiel utilise des exceptions pour implémenter des fonctionnalités telles que l’annulation. Par conséquent, écrivez du code de protégée contre les exceptions lorsque vous appelez le runtime ou une autre bibliothèque qui appelle le runtime.

Le *Resource Acquisition Is Initialization* modèle (RAII) est une façon de gérer en toute sécurité la durée de vie d’un objet d’accès concurrentiel dans une portée donnée. Dans le modèle RAII, une structure de données est allouée sur la pile. Cette structure de données initialise ou acquiert une ressource lorsqu’il est créé et détruit ou libère cette ressource lorsque la structure de données est détruite. Le modèle RAII garantit que le destructeur est appelé avant la fermeture de la portée englobante. Ce modèle est utile lorsqu’une fonction contient plusieurs `return` instructions. Ce modèle vous permet également d’écrire du code d’exception-safe. Quand un `throw` instruction provoque la pile de déroulement, le destructeur pour l’objet RAII est appelé ; par conséquent, la ressource est toujours correctement supprimée ou publiée.

Le runtime définit plusieurs classes qui utilisent le modèle RAII, par exemple, [Concurrency::critical_section :: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) et [Concurrency::reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Ces classes d’assistance sont appelées *verrous à portée limitée*. Ces classes offrent plusieurs avantages lorsque vous travaillez avec [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) ou [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objets. Le constructeur de ces classes acquiert l’accès à la collection `critical_section` ou `reader_writer_lock` objet ; l’accès de versions de destructeur à cet objet. Car un verrou à portée limitée libère automatiquement l’accès à son objet d’exclusion mutuelle lorsqu’il est détruit, vous ne déverrouillez pas manuellement l’objet sous-jacent.

Considérons la classe suivante, `account`, qui est défini par une bibliothèque externe et ne peut donc pas être modifié.

[!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]

L’exemple suivant effectue plusieurs transactions sur un `account` objet en parallèle. L’exemple utilise un `critical_section` objet pour synchroniser l’accès à la `account` de l’objet, car le `account` classe n’est pas un accès concurrentiel sécurisé. Chaque opération parallèle utilise un `critical_section::scoped_lock` objet afin de garantir que le `critical_section` objet est déverrouillé lorsque l’opération réussit ou échoue. Lorsque le solde du compte est négatif, le `withdraw` opération échoue en levant une exception.

[!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]

Cet exemple produit la sortie suivante :

```Output
Balance before deposit: 1924
Balance after deposit: 2924
Balance before withdrawal: 2924
Balance after withdrawal: -76
Balance before withdrawal: -76
Error details:
    negative balance: -76
```

Pour obtenir des exemples supplémentaires qui utilisent le modèle RAII pour gérer la durée de vie des objets d’accès concurrentiel, consultez [procédure pas à pas : Suppression de travail d’un Thread d’Interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [Comment : Utiliser la classe Context pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md), et [Comment : Utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

[[Haut](#top)]

##  <a name="global-scope"></a> Ne créez pas d’objets d’accès concurrentiel dans une portée globale

Lorsque vous créez un objet d’accès concurrentiel dans une portée globale vous pouvez provoquer des problèmes de blocage ou de la mémoire des violations d’accès peut se produire dans votre application.

Par exemple, lorsque vous créez un objet de Runtime d’accès concurrentiel, le runtime crée un planificateur par défaut si aucune n’a été pas encore créée. Un objet de runtime qui est créé pendant la construction de l’objet global entraîne en conséquence le runtime crée ce planificateur par défaut. Toutefois, ce processus prend un verrou interne, ce qui peut interférer avec l’initialisation d’autres objets qui prennent en charge l’infrastructure du Runtime d’accès concurrentiel. Ce verrou interne peut être requis par un autre objet d’infrastructure qui n’a pas encore été initialisé et peut donc provoquer un interblocage dans votre application.

L’exemple suivant illustre la création d’un global [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objet. Ce modèle s’applique non seulement à la `Scheduler` classe mais tous les autres types fournis par le Runtime d’accès concurrentiel. Nous recommandons que vous ne suivez pas ce modèle, car cela peut entraîner un comportement inattendu dans votre application.

[!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]

Pour obtenir des exemples de la méthode correcte pour créer `Scheduler` , consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

[[Haut](#top)]

##  <a name="shared-data"></a> N’utilisez pas les objets d’accès concurrentiel dans les Segments de données partagées

Le Runtime d’accès concurrentiel ne prend pas en charge l’utilisation d’objets d’accès concurrentiel dans une section de données partagées, par exemple, une section de données qui est créée par le [data_seg](../../preprocessor/data-seg.md) `#pragma` directive. Un objet d’accès concurrentiel qui est partagé entre les limites de processus est susceptible de l’exécution dans un état incohérent ou non valide.

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Bonnes pratiques sur le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)<br/>
[Comparaison des structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)<br/>
[Guide pratique pour utiliser Alloc et Free afin d’améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)<br/>
[Guide pratique pour utiliser le surabonnement afin de compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)<br/>
[Guide pratique pour utiliser la classe de contexte pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Procédure pas à pas : suppression de travail d’un thread d’interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)<br/>
[Bonnes pratiques de la Bibliothèque de modèles parallèles](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Bonnes pratiques pour la bibliothèque d’agents asynchrones](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
