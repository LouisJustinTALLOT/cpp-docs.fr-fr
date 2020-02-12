---
title: Contextes
ms.date: 11/04/2016
helpviewer_keywords:
- contexts [Concurrency Runtime]
ms.assetid: 10c1d861-8fbb-4ba0-b2ec-61876b11176e
ms.openlocfilehash: 9eaf21a3d65ae891a48657de9d3e7aff78ce12b9
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142188"
---
# <a name="contexts"></a>Contextes

Ce document décrit le rôle des contextes dans le runtime d’accès concurrentiel. Un thread attaché à un planificateur est connu sous le nom de *contexte d’exécution*, ou simplement de *contexte*. La fonction [Concurrency :: wait](reference/concurrency-namespace-functions.md#wait) et la classe Concurrency ::[Context](../../parallel/concrt/reference/context-class.md) vous permettent de contrôler le comportement des contextes. Utilisez la fonction `wait` pour interrompre le contexte actuel pendant une période spécifiée. Utilisez la classe `Context` lorsque vous avez besoin de davantage de contrôle sur le blocage, le déblocage et le rendement des contextes, ou lorsque vous souhaitez surabonner le contexte actuel.

> [!TIP]
> Le runtime d'accès concurrentiel fournit un planificateur par défaut, et vous n'êtes donc pas obligé d'en créer un dans votre application. Étant donné que le Planificateur de tâches vous aide à ajuster les performances de vos applications, nous vous recommandons de commencer avec la [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md) ou la [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) si vous débutez avec le runtime d’accès concurrentiel.

## <a name="the-wait-function"></a>La fonction Wait

La fonction [Concurrency :: wait](reference/concurrency-namespace-functions.md#wait) produit de manière coopérative l’exécution du contexte actuel pendant un nombre de millisecondes spécifié. Le runtime utilise le temps de production pour effectuer d’autres tâches. Une fois le temps spécifié écoulé, le runtime replanifie l’exécution du contexte. Par conséquent, la fonction `wait` peut suspendre le contexte actuel plus longtemps que la valeur fournie pour le paramètre `milliseconds`.

Si vous passez 0 (zéro) pour le paramètre `milliseconds`, le runtime suspend le contexte actuel jusqu’à ce que tous les autres contextes actifs aient la possibilité d’effectuer le travail. Cela vous permet de générer une tâche pour toutes les autres tâches actives.

### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise la fonction `wait` pour générer le contexte actuel et permettre ainsi l’exécution d’autres contextes, consultez [Comment : utiliser des groupes de planification pour influencer l’ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md).

## <a name="the-context-class"></a>Classe de contexte

La classe Concurrency ::[Context](../../parallel/concrt/reference/context-class.md) fournit une abstraction de programmation pour un contexte d’exécution et offre deux fonctionnalités importantes : la possibilité de bloquer, débloquer et générer le contexte actuel de manière coopérative, ainsi que la possibilité de surabonner le contexte actuel.

### <a name="cooperative-blocking"></a>Blocage coopératif

La classe `Context` vous permet de bloquer ou de générer le contexte d’exécution actuel. Le blocage ou le produit est utile lorsque le contexte actuel ne peut pas continuer car une ressource n’est pas disponible.

La méthode [Concurrency :: Context :: Block](reference/context-class.md#block) bloque le contexte actuel. Un contexte bloqué produit ses ressources de traitement afin que le runtime puisse exécuter d’autres tâches. La méthode [Concurrency :: Context :: Deblock](reference/context-class.md#unblock) débloque un contexte bloqué. La méthode `Context::Unblock` doit être appelée à partir d’un contexte différent de celui qui a appelé `Context::Block`. Le runtime lève [Concurrency :: context_self_unblock](../../parallel/concrt/reference/context-self-unblock-class.md) si un contexte tente de se débloquer.

Pour bloquer et débloquer un contexte de manière coopérative, vous appelez généralement [Concurrency :: Context :: CurrentContext](reference/context-class.md#currentcontext) pour récupérer un pointeur vers l’objet `Context` associé au thread actuel et enregistrer le résultat. Vous appelez ensuite la méthode `Context::Block` pour bloquer le contexte actuel. Ensuite, appelez `Context::Unblock` à partir d’un contexte distinct pour débloquer le contexte bloqué.

Vous devez faire correspondre chaque paire d’appels à `Context::Block` et `Context::Unblock`. Le runtime lève [Concurrency :: context_unblock_unbalanced](../../parallel/concrt/reference/context-unblock-unbalanced-class.md) lorsque la méthode `Context::Block` ou `Context::Unblock` est appelée consécutivement sans appel correspondant à l’autre méthode. Toutefois, il n’est pas nécessaire d’appeler `Context::Block` avant d’appeler `Context::Unblock`. Par exemple, si un contexte appelle `Context::Unblock` avant qu’un autre contexte n’appelle `Context::Block` pour le même contexte, ce contexte reste débloqué.

La méthode [Concurrency :: Context :: Yield](reference/context-class.md#yield) produit l’exécution afin que le runtime puisse exécuter d’autres tâches, puis replanifier l’exécution du contexte. Lorsque vous appelez la méthode `Context::Block`, le runtime ne replanifie pas le contexte.

#### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise les méthodes `Context::Block`, `Context::Unblock`et `Context::Yield` pour implémenter une classe de sémaphore coopérative, consultez [Comment : utiliser la classe Context pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

##### <a name="oversubscription"></a>Surabonnement

Le planificateur par défaut crée le même nombre de threads qu’il y a de threads matériels disponibles. Vous pouvez utiliser le *surabonnement* pour créer des threads supplémentaires pour un thread matériel donné.

Pour les opérations nécessitant de nombreuses ressources de calcul, le surabonnement n’est généralement pas mis à l’échelle, car il introduit une surcharge supplémentaire. Toutefois, pour les tâches qui présentent une latence élevée, par exemple la lecture de données à partir d’un disque ou d’une connexion réseau, le surabonnement peut améliorer l’efficacité globale de certaines applications.

> [!NOTE]
> Activez le surabonnement uniquement à partir d’un thread créé par l’runtime d’accès concurrentiel. Le surabonnement n’a aucun effet lorsqu’il est appelé à partir d’un thread qui n’a pas été créé par le runtime (y compris le thread principal).

Pour activer le surabonnement dans le contexte actuel, appelez la méthode [Concurrency :: Context :: Oversubscribe](reference/context-class.md#oversubscribe) avec le paramètre `_BeginOversubscription` défini sur **true**. Lorsque vous activez le surabonnement sur un thread créé par le runtime d’accès concurrentiel, le runtime crée un thread supplémentaire. Une fois que toutes les tâches nécessitant un surabonnement sont terminées, appelez `Context::Oversubscribe` avec le paramètre `_BeginOversubscription` défini sur **false**.

Vous pouvez activer le surabonnement plusieurs fois à partir du contexte actuel, mais vous devez le désactiver le même nombre de fois que vous l’activez. Le surabonnement peut également être imbriqué ; autrement dit, une tâche créée par une autre tâche qui utilise le surabonnement peut également surabonner son contexte. Toutefois, si une tâche imbriquée et son parent appartiennent au même contexte, seul l’appel le plus à l’extérieur à `Context::Oversubscribe` entraîne la création d’un thread supplémentaire.

> [!NOTE]
> Le runtime lève [Concurrency :: invalid_oversubscribe_operation](../../parallel/concrt/reference/invalid-oversubscribe-operation-class.md) si le surabonnement est désactivé avant qu’il ne soit activé.

###### <a name="example"></a>Exemple

Pour obtenir un exemple qui utilise le surabonnement pour compenser la latence provoquée par la lecture de données à partir d’une connexion réseau, consultez [Comment : utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md).

## <a name="see-also"></a>Voir aussi

[Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md)<br/>
[Guide pratique pour utiliser des groupes de planification pour influencer l’ordre d’exécution](../../parallel/concrt/how-to-use-schedule-groups-to-influence-order-of-execution.md)<br/>
[Guide pratique pour utiliser la classe Context pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md)<br/>
[Guide pratique pour utiliser le surabonnement pour compenser la latence](../../parallel/concrt/how-to-use-oversubscription-to-offset-latency.md)
