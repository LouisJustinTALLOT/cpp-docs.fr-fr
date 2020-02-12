---
title: Fonctions de passage de messages
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 4e1052a59f355c4ad5a7c6b57724268c24a209b4
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143298"
---
# <a name="message-passing-functions"></a>Fonctions de passage de messages

La bibliothèque d’agents asynchrones fournit plusieurs fonctions qui vous permettent de transmettre des messages entre les composants.

Ces fonctions de passage de message sont utilisées avec les différents types de blocs de message. Pour plus d’informations sur les types de blocs de messages définis par le runtime d’accès concurrentiel, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="top"></a> Sections

Cette rubrique décrit les fonctions de passage de message suivantes :

- [Send et asend](#send)

- [réception et try_receive](#receive)

- [Exemples](#examples)

## <a name="send"></a>Send et asend

La fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) envoie un message à la cible spécifiée de façon synchrone et la fonction [Concurrency :: asend](reference/concurrency-namespace-functions.md#asend) envoie un message à la cible spécifiée de manière asynchrone. Les fonctions `send` et `asend` attendent que la cible indique qu’elle accepte ou refuse le message.

La fonction `send` attend que la cible accepte ou refuse le message avant qu’elle soit retournée. La fonction `send` retourne la **valeur true** si le message a été remis et **false** dans le cas contraire. Étant donné que la fonction `send` fonctionne de façon synchrone, la fonction `send` attend que la cible reçoive le message avant de retourner.

À l’inverse, la fonction `asend` n’attend pas que la cible accepte ou refuse le message avant de retourner. Au lieu de cela, la fonction `asend` retourne la **valeur true** si la cible accepte le message et la prendra finalement. Dans le cas contraire, `asend` retourne la **valeur false** pour indiquer que la cible a refusé le message ou a différé la décision de prendre le message.

[[Haut](#top)]

## <a name="receive"></a>réception et try_receive

Les fonctions [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) et [Concurrency :: try_receive](reference/concurrency-namespace-functions.md#try_receive) lisent les données d’une source donnée. La fonction `receive` attend que les données deviennent disponibles, tandis que la fonction `try_receive` retourne immédiatement.

Utilisez la fonction `receive` lorsque vous devez disposer des données pour continuer. Utilisez la fonction `try_receive` si vous ne devez pas bloquer le contexte actuel ou si vous n’avez pas besoin de disposer des données pour continuer.

[[Haut](#top)]

## <a name="examples"></a> Exemples

Pour obtenir des exemples qui utilisent les fonctions `send` et `asend`et `receive`, consultez les rubriques suivantes :

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Guide pratique pour implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Guide pratique pour fournir des fonctions de travail aux classes call et transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Guide pratique pour utiliser la classe transformer dans un pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Guide pratique pour effectuer une sélection parmi les tâches terminées](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Guide pratique pour envoyer un message à intervalles réguliers](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Guide pratique pour utiliser un filtre de bloc de message](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Send, fonction](reference/concurrency-namespace-functions.md#send)<br/>
[asend, fonction](reference/concurrency-namespace-functions.md#asend)<br/>
[Receive, fonction](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive fonction)](reference/concurrency-namespace-functions.md#try_receive)
