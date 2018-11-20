---
title: bibliothèque d’agents asynchrones
ms.date: 11/19/2018
helpviewer_keywords:
- Agents Library
- Asynchronous Agents Library
ms.assetid: d2a72a31-8ba6-4220-ad7a-e403a6acaa42
ms.openlocfilehash: 8b4e8e6489e98aadb6ea41d32d5a9ba14efe2668
ms.sourcegitcommit: 9e891eb17b73d98f9086d9d4bfe9ca50415d9a37
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2018
ms.locfileid: "52175858"
---
# <a name="asynchronous-agents-library"></a>bibliothèque d’agents asynchrones

La bibliothèque d’Agents asynchrones (ou simplement *bibliothèque d’Agents*) fournit un modèle de programmation qui vous permet d’augmenter la robustesse du développement d’applications d’accès concurrentiel. La bibliothèque d’Agents est une bibliothèque de modèles C++ qui encourage un modèle de programmation basé sur acteur et les messages in-process en passant de flux de données à granularité grossière et les tâches de traitement « pipeline ». La bibliothèque d’Agents s’appuie sur les composants de gestion des ressources et de planification du Runtime d’accès concurrentiel.

## <a name="programming-model"></a>Modèle de programmation

La bibliothèque d’Agents fournit des alternatives à l’état partagé en vous permettant de connecter des composants isolés via un modèle de communication asynchrone basé sur les flux de données au lieu de flux de contrôle. *Flux de données* fait référence à une programmation modèle où les calculs sont effectués lorsque toutes les données requises est disponible ; *flux de contrôle* fait référence à un modèle de programmation où les calculs sont effectués dans un ordre prédéterminé.

Le modèle de programmation de flux de données est lié au concept de *transmission de messages*, durant laquelle les composants indépendants d’un programme communiquent entre eux à l’aide de messages.

La bibliothèque d’Agents est composée de trois composants : *agents asynchrones*, *blocs de messages asynchrones*, et *des fonctions de passage de messages*. Agents de maintiennent l’état et utilisent des blocs de messages et des fonctions de passage de messages pour communiquer entre eux et avec les composants externes. Fonctions de passage de messages permettent aux agents d’envoyer et recevoir des messages vers et depuis les composants externes. Blocs de messages asynchrones stockent des messages et activer les agents de communiquer de manière synchronisée.

L’illustration suivante montre comment deux agents, utilisez des blocs de messages et des fonctions de passage de messages pour communiquer. Dans cette illustration, `agent1` envoie un message à `agent2` à l’aide de la [concurrency::send](reference/concurrency-namespace-functions.md#send) (fonction) et un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objet. `agent2` utilise le [concurrency::receive](reference/concurrency-namespace-functions.md#receive) fonction permettant de lire le message. `agent2` utilise la même méthode pour envoyer un message à `agent1`. Flèches en pointillés représentent le flux de données entre les agents. Flèches pleines connectent les agents aux blocs de messages qui ils écrire ou de lire à partir de.

![Les composants de la bibliothèque d’Agents](../../parallel/concrt/media/agent_librarycomp.png "les composants de la bibliothèque d’Agents")

Un exemple de code qui implémente cette illustration est présenté plus loin dans cette rubrique.

Le modèle de programmation de l’agent a plusieurs avantages par rapport autres mécanismes d’accès concurrentiel et la synchronisation, par exemple, les événements. L’un des avantages sont qu’à l’aide de transmission de messages pour transmettre les modifications d’état entre des objets, vous pouvez isoler l’accès aux ressources partagées et ainsi améliorer l’évolutivité. L’avantage de passage de messages est la synchronisation des données au lieu de lier le contenu à un objet de synchronisation externe. Cela simplifie la transmission de données entre les composants et que vous pouvez éliminer les erreurs de programmation dans vos applications.

## <a name="when-to-use-the-agents-library"></a>Quand utiliser la bibliothèque d’Agents

Utilisez la bibliothèque d’Agents lorsque vous avez plusieurs opérations qui doivent communiquer entre eux de façon asynchrone. Blocs de messages et des fonctions de passage de messages vous permettent d’écrire des applications parallèles sans nécessiter de mécanismes de synchronisation tels que les verrous. Ainsi vous concentrer sur la logique d’application.

Le modèle de programmation de l’agent est souvent utilisé pour créer *des pipelines de données* ou *réseaux*. Un pipeline de données est une série de composants, chacun d’eux exécute une tâche spécifique qui contribue à un plus grand objectif. Chaque composant dans un pipeline de flux de données effectue un travail lorsqu’il reçoit un message à partir d’un autre composant. Le résultat de ce travail est passé à d’autres composants dans le pipeline ou d’un réseau. Les composants peuvent utiliser plus de fonctionnalités affinent la concurrence des autres bibliothèques, par exemple, le [bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md).

## <a name="example"></a>Exemple

L’exemple suivant implémente l’illustration indiquée plus haut dans cette rubrique.

[!code-cpp[concrt-basic-agents#1](../../parallel/concrt/codesnippet/cpp/asynchronous-agents-library_1.cpp)]

Cet exemple génère la sortie suivante :

```Output
agent1: sending request...
agent2: received 'request'.
agent2: sending response...
agent1: received '42'.
```

Les rubriques suivantes décrivent les fonctionnalités utilisées dans cet exemple.

## <a name="related-topics"></a>Rubriques connexes

[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br/>
Décrit le rôle des agents asynchrones dans la résolution des plus grandes tâches de calculs.

[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
Décrit les différents types de blocs de messages qui sont fournis par la bibliothèque d’Agents.

[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
Décrit les différentes routines de passage de message sont fournies par la bibliothèque d’Agents.

[Guide pratique pour implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)<br/>
Décrit comment implémenter le modèle de producteur-consommateur dans votre application.

[Guide pratique pour fournir des fonctions de travail aux classes call et transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)<br/>
Illustre plusieurs méthodes pour fournir des fonctions de travail pour le [concurrency::call](../../parallel/concrt/reference/call-class.md) et [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) classes.

[Guide pratique pour utiliser la classe transformer dans un pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)<br/>
Montre comment utiliser le [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) classe dans un pipeline de données.

[Guide pratique pour effectuer une sélection parmi les tâches terminées](../../parallel/concrt/how-to-select-among-completed-tasks.md)<br/>
Montre comment utiliser le [classes concurrency::choice](../../parallel/concrt/reference/choice-class.md) et [concurrency::join](../../parallel/concrt/reference/join-class.md) classes pour sélectionner la première tâche afin de terminer un algorithme de recherche.

[Guide pratique pour envoyer un message à intervalles réguliers](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)<br/>
Montre comment utiliser le [concurrency::timer](../../parallel/concrt/reference/timer-class.md) classe pour envoyer un message à intervalles réguliers.

[Guide pratique pour utiliser un filtre de bloc de message](../../parallel/concrt/how-to-use-a-message-block-filter.md)<br/>
Montre comment utiliser un filtre pour permettre à un bloc de message asynchrone accepter ou rejeter les messages.

[Bibliothèque de modèles parallèles (PPL)](../../parallel/concrt/parallel-patterns-library-ppl.md)<br/>
Décrit comment utiliser différents modèles parallèles, tels que les algorithmes parallèles, dans vos applications.

[Le runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime.md)<br/>
Décrit le runtime d'accès concurrentiel, qui simplifie la programmation parallèle, et contient des liens vers les rubriques connexes.

