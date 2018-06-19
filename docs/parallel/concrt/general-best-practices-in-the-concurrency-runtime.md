---
title: Meilleures pratiques en général dans le Runtime d’accès concurrentiel | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Concurrency Runtime, general best practices
ms.assetid: ce5c784c-051e-44a6-be84-8b3e1139c18b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a2cd9cffa76ce179f478422af9c8efce380a2465
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694116"
---
# <a name="general-best-practices-in-the-concurrency-runtime"></a>Meilleures pratiques en général du runtime d’accès concurrentiel
Ce document décrit les meilleures pratiques qui s’appliquent à plusieurs zones du Runtime d’accès concurrentiel.  
  
##  <a name="top"></a> Sections  
 Ce document contient les sections suivantes :  
  
- [Utiliser des éléments de synchronisation coopérative lorsque cela est Possible](#synchronization)  
  
- [Éviter les tâches longues qui ne pas Yield](#yield)  
  
- [Utiliser le surabonnement pour compenser les opérations qui bloquent ou présenter une latence élevée](#oversubscription)  
  
- [Utiliser les fonctions de gestion de mémoire simultanés lorsque cela est Possible](#memory)  
  
- [Utiliser RAII pour gérer la durée de vie des objets d’accès concurrentiel](#raii)  
  
- [Ne créez pas d’objets d’accès concurrentiel dans une portée globale](#global-scope)  
  
- [N’utilisez pas les objets d’accès concurrentiel dans les Segments de données partagées](#shared-data)  
  
##  <a name="synchronization"></a> Utiliser des éléments de synchronisation coopérative lorsque cela est Possible  
 Le Runtime d’accès concurrentiel fournit de nombreuses constructions d’accès concurrentiel sécurisé qui ne nécessitent pas d’un objet de synchronisation externe. Par exemple, le [concurrency::concurrent_vector](../../parallel/concrt/reference/concurrent-vector-class.md) classe fournit concurrentiel ajouter et élément accéder aux opérations. Toutefois, pour les cas où vous avez besoin d’un accès exclusif à une ressource, le runtime fournit la [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md), et [concurrence :: événement](../../parallel/concrt/reference/event-class.md) classes. Ces types se comportent de manière coopérative ; Par conséquent, le Planificateur de tâches peut réaffecter les ressources de traitement à un autre contexte que la première tâche attend des données. Si possible, utilisez ces types de synchronisation au lieu d’autres mécanismes de synchronisation, telles que celles fournies par l’API Windows, qui ne fonctionnent pas de manière coopérative. Pour plus d’informations sur ces types de synchronisation et un exemple de code, consultez [des Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md) et [comparaison des Structures de données de synchronisation de l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md).  
  
 [[Haut](#top)]  
  
##  <a name="yield"></a> Éviter les tâches longues qui ne pas Yield  
 Étant donné que le Planificateur de tâches se comporte de manière coopérative, il ne fournit pas équité entre des tâches. Par conséquent, une tâche peut empêcher d’autres tâches de démarrage. Bien que cela soit acceptable dans certains cas, dans d’autres cas, cela peut provoquer un blocage ou la privation.  
  
 L’exemple suivant effectue plusieurs tâches que le nombre de ressources de traitement allouées. Ne génère pas de la première tâche du Planificateur de tâches et par conséquent, la seconde tâche ne démarre pas tant que la première tâche se termine.  
  
 [!code-cpp[concrt-cooperative-tasks#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_1.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
 1: 250000000 1: 500000000 1: 750000000 1: 1000000000 2: 250000000 2: 500000000 2: 750000000 2: 1000000000  
  

 Il existe plusieurs façons d’activer la coopération entre les deux tâches. Une façon consiste à céder occasionnellement au planificateur de tâches dans une tâche d’exécution longue. L’exemple suivant modifie le `task` fonction à appeler le [Concurrency::Context :: yield](reference/context-class.md#yield) méthode à céder l’exécution au planificateur de tâches afin qu’une autre tâche peut s’exécuter.  

  
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
  
 Le `Context::Yield` méthode ne produit qu’un autre thread actif dans le planificateur auquel le thread actuel appartient, une tâche légère ou un autre thread de système d’exploitation. Cette méthode ne génère pas de travail qui est planifiée pour s’exécuter un [concurrency::task_group](reference/task-group-class.md) ou [concurrency::structured_task_group](../../parallel/concrt/reference/structured-task-group-class.md) de l’objet mais n’a pas encore démarré.  
  
 Autres manières d’activer la coopération entre les tâches longues. Vous pouvez interrompre une grande tâche en sous-tâches plus petites. Vous pouvez également activer le surabonnement pendant une tâche de longue durée. Le surabonnement vous permet de créer un nombre de threads plus important que le nombre de threads matériels disponibles. Le surabonnement est particulièrement utile lorsqu’une tâche de longue durée contient une grande quantité de latence, par exemple, la lecture des données à partir du disque ou d’une connexion réseau. Pour plus d’informations sur les tâches légères et le surabonnement, consultez [du Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Haut](#top)]  
  
##  <a name="oversubscription"></a> Utiliser le surabonnement pour compenser les opérations qui bloquent ou présenter une latence élevée  
 Le Runtime d’accès concurrentiel fournit des primitives de synchronisation, tels que [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md), qui permettent de tâches bloquer de manière coopérative et génèrent les uns aux autres. Lorsqu’une tâche en coopération bloque ou génère, le Planificateur de tâches peut réaffecter les ressources de traitement à un autre contexte que la première tâche attend des données.  
  
 Il existe des cas dans lequel vous ne pouvez pas utiliser le mécanisme de blocage coopératif qui est fourni par le Runtime d’accès concurrentiel. Par exemple, une bibliothèque externe que vous utilisez peut utiliser un mécanisme de synchronisation différents. Un autre exemple est lorsque vous effectuez une opération qui peut avoir un degré élevé de latence, par exemple, lorsque vous utilisez l’API Windows `ReadFile` fonction permettant de lire des données à partir d’une connexion réseau. Dans ce cas, le surabonnement peut permettre d’autres tâches à exécuter quand une autre tâche est inactive. Le surabonnement vous permet de créer un nombre de threads plus important que le nombre de threads matériels disponibles.  
  
 Considérez la fonction suivante, `download`, qui télécharge le fichier à l’URL donnée. Cet exemple utilise le [Concurrency::Context :: Oversubscribe](reference/context-class.md#oversubscribe) méthode pour augmenter provisoirement le nombre de threads actifs.  

 [!code-cpp[concrt-download-oversubscription#4](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_3.cpp)]  
  
 Étant donné que le `GetHttpFile` fonction effectue une opération potentiellement latente, le surabonnement peut permettre d’autres tâches à exécuter pendant que la tâche actuelle attend des données. Pour obtenir la version complète de cet exemple, consultez [Comment : surabonnement utilisez à la latence de décalage](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 [[Haut](#top)]  
  
##  <a name="memory"></a> Utiliser les fonctions de gestion de mémoire simultanés lorsque cela est Possible  

 Utilisez les fonctions de gestion de mémoire, [concurrency::Alloc](reference/concurrency-namespace-functions.md#alloc) et [concurrency::Free](reference/concurrency-namespace-functions.md#free), lorsque vous avez des tâches affinées qui allouent fréquemment de petits objets qui ont une durée de vie relativement courte. Le Runtime d’accès concurrentiel maintient un cache mémoire séparé pour chaque thread en cours d’exécution. Le `Alloc` et `Free` fonctions allouent et libèrent la mémoire à partir de ces caches sans utiliser de verrous ou de barrières de mémoire.  
  
 Pour plus d’informations sur ces fonctions de gestion de mémoire, consultez [du Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md). Pour obtenir un exemple qui utilise ces fonctions, consultez [Comment : utiliser Alloc et Free pour améliorer les performances de mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md).  
  
 [[Haut](#top)]  
  
##  <a name="raii"></a> Utiliser RAII pour gérer la durée de vie des objets d’accès concurrentiel  
 Le Runtime d’accès concurrentiel utilise la gestion des exceptions pour implémenter des fonctionnalités telles que l’annulation. Par conséquent, écrivez un programme contre les exceptions lorsque vous appelez le runtime ou une autre bibliothèque qui appelle le runtime.  
  
 Le *Resource Acquisition Is Initialization* modèle (RAII) consiste à gérer en toute sécurité la durée de vie d’un objet d’accès concurrentiel sous une étendue donnée. Selon le modèle RAII, une structure de données est allouée sur la pile. Cette structure de données initialise ou acquiert une ressource lorsqu’il est créé et détruit ou libère cette ressource lorsque la structure de données est détruite. Le modèle RAII garantit que le destructeur est appelé avant la fermeture de la portée englobante. Ce modèle est utile lorsqu’une fonction contient plusieurs `return` instructions. Ce modèle vous permet également d’écrire du code sécurisé à l’exception. Lorsqu’un `throw` instruction provoque la pile de déroulement, le destructeur pour l’objet RAII est appelé ; par conséquent, la ressource est toujours correctement supprimée ou libérée.  
  
 Le runtime définit plusieurs classes qui utilisent le modèle RAII, par exemple, [Concurrency::critical_section :: scoped_lock](../../parallel/concrt/reference/critical-section-class.md#critical_section__scoped_lock_class) et [Concurrency::reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class). Ces classes d’assistance sont appelés *verrous à portée limitée*. Ces classes offrent plusieurs avantages lorsque vous travaillez avec [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) ou [concurrency::reader_writer_lock](../../parallel/concrt/reference/reader-writer-lock-class.md) objets. Le constructeur de ces classes acquiert l’accès à la collection `critical_section` ou `reader_writer_lock` objet ; l’accès de versions de destructeur à cet objet. Car un verrou à portée limitée libère automatiquement l’accès à son objet d’exclusion mutuelle lorsqu’il est détruit, vous ne déverrouillez pas manuellement l’objet sous-jacent.  
  
 Considérons la classe suivante, `account`, qui est défini par une bibliothèque externe et ne peut donc pas être modifié.  
  
 [!code-cpp[concrt-account-transactions#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_4.h)]  
  
 L’exemple suivant effectue plusieurs transactions sur une `account` objet en parallèle. L’exemple utilise un `critical_section` objet pour synchroniser l’accès à la `account` de l’objet, car le `account` classe n’est pas d’accès concurrentiel sécurisé. Chaque opération parallèle utilise un `critical_section::scoped_lock` objet afin de garantir que le `critical_section` objet est déverrouillé lorsque l’opération réussit ou échoue. Lorsque le solde du compte est négatif, la `withdraw` échoue en levant une exception.  
  
 [!code-cpp[concrt-account-transactions#2](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_5.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
Balance before deposit: 1924  
Balance after deposit: 2924  
Balance before withdrawal: 2924  
Balance after withdrawal: -76  
Balance before withdrawal: -76  
Error details:  
    negative balance: -76  
```  
  
 Pour obtenir des exemples supplémentaires qui utilisent le modèle RAII pour gérer la durée de vie des objets d’accès concurrentiel, consultez [procédure pas à pas : suppression de travail d’un Thread d’Interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md), [Comment : utiliser la classe Context pour implémenter une coopérative Sémaphore](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md), et [Comment : utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).  
  
 [[Haut](#top)]  
  
##  <a name="global-scope"></a> Ne créez pas d’objets d’accès concurrentiel dans une portée globale  
 Lorsque vous créez un objet d’accès concurrentiel dans une portée globale risque de problèmes de blocage ou de la mémoire des violations d’accès se produise dans votre application.  
  
 Par exemple, lorsque vous créez un objet de Runtime d’accès concurrentiel, le runtime crée un planificateur par défaut s’il n’a pas encore créé. Un objet de runtime qui est créé pendant la construction de l’objet global en conséquence entraîne le runtime créer ce planificateur par défaut. Toutefois, ce processus utilise un verrou interne, ce qui peut interférer avec l’initialisation d’autres objets qui prennent en charge l’infrastructure du Runtime d’accès concurrentiel. Ce verrou interne peut être requis par un autre objet d’infrastructure qui n’a pas encore été initialisé et peut provoquer ainsi un interblocage dans votre application.  
  
 L’exemple suivant illustre la création d’un élément global [concurrency::Scheduler](../../parallel/concrt/reference/scheduler-class.md) objet. Ce modèle s’applique non seulement à la `Scheduler` classe, mais tous les autres types fournis par le Runtime d’accès concurrentiel. Nous recommandons que vous ne suivez pas ce modèle, car elle peut provoquer un comportement inattendu dans votre application.  
  
 [!code-cpp[concrt-global-scheduler#1](../../parallel/concrt/codesnippet/cpp/general-best-practices-in-the-concurrency-runtime_6.cpp)]  
  
 Pour obtenir des exemples de la méthode correcte pour créer `Scheduler` , consultez [du Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  
 [[Haut](#top)]  
  
##  <a name="shared-data"></a> N’utilisez pas les objets d’accès concurrentiel dans les Segments de données partagées  
 Le Runtime d’accès concurrentiel ne prend pas en charge l’utilisation des objets d’accès concurrentiel dans une section de données partagées, par exemple, une section de données qui est créée par le [data_seg](../../preprocessor/data-seg.md) `#pragma` la directive. Un objet d’accès concurrentiel qui est partagé entre les limites de processus est susceptible de l’exécution dans un état incohérent ou non valide.  
  
 [[Haut](#top)]  
  
## <a name="see-also"></a>Voir aussi  
 [Meilleures pratiques de Runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md)   
 [Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)   
 [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)   
 [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)   
 [Comparaison des Structures de données de synchronisation avec l’API Windows](../../parallel/concrt/comparing-synchronization-data-structures-to-the-windows-api.md)   
 [Comment : utiliser Alloc et Free pour améliorer les performances de la mémoire](../../parallel/concrt/how-to-use-alloc-and-free-to-improve-memory-performance.md)   
 [Comment : utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)   
 [Comment : utiliser la classe Context pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)   
 [Procédure pas à pas : Suppression de travail d’un Thread d’Interface utilisateur](../../parallel/concrt/walkthrough-removing-work-from-a-user-interface-thread.md)   
 [Meilleures pratiques de la bibliothèque de modèles parallèles](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Bonnes pratiques pour la bibliothèque d’agents asynchrones](../../parallel/concrt/best-practices-in-the-asynchronous-agents-library.md)
