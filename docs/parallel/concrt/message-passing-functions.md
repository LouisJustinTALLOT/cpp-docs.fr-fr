---
title: Fonctions de passage de messages
ms.date: 11/04/2016
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
ms.openlocfilehash: 3709e7b5280b96b2b77ec850a06ed15d0e42a7e5
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87194626"
---
# <a name="message-passing-functions"></a>Fonctions de passage de messages

La bibliothèque d’agents asynchrones fournit plusieurs fonctions qui vous permettent de transmettre des messages entre les composants.

Ces fonctions de passage de message sont utilisées avec les différents types de blocs de message. Pour plus d’informations sur les types de blocs de messages définis par le runtime d’accès concurrentiel, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="sections"></a><a name="top"></a>Sections

Cette rubrique décrit les fonctions de passage de message suivantes :

- [Send et asend](#send)

- [réception et try_receive](#receive)

- [Exemples](#examples)

## <a name="send-and-asend"></a><a name="send"></a>Send et asend

La fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) envoie un message à la cible spécifiée de façon synchrone et la fonction [Concurrency :: asend](reference/concurrency-namespace-functions.md#asend) envoie un message à la cible spécifiée de manière asynchrone. Les `send` fonctions et `asend` s’attendent à ce que la cible indique qu’elle accepte ou refuse le message.

La `send` fonction attend que la cible accepte ou refuse le message avant qu’elle soit retournée. La `send` fonction retourne **`true`** si le message a été remis et dans le **`false`** cas contraire. Étant donné que la `send` fonction fonctionne de façon synchrone, la `send` fonction attend que la cible reçoive le message avant de retourner.

Inversement, la `asend` fonction n’attend pas que la cible accepte ou refuse le message avant de retourner. Au lieu de `asend` cela, la fonction retourne **`true`** si la cible accepte le message et le prendra finalement. Sinon, `asend` retourne **`false`** pour indiquer que la cible a refusé le message ou a différé la décision de prendre le message.

[[Haut](#top)]

## <a name="receive-and-try_receive"></a><a name="receive"></a>réception et try_receive

Les fonctions [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) et [Concurrency :: try_receive](reference/concurrency-namespace-functions.md#try_receive) lisent les données d’une source donnée. La `receive` fonction attend que les données deviennent disponibles, tandis que la `try_receive` fonction est retournée immédiatement.

Utilisez la `receive` fonction lorsque vous devez disposer des données pour continuer. Utilisez la `try_receive` fonction si vous ne devez pas bloquer le contexte actuel ou si vous n’avez pas besoin de disposer des données pour continuer.

[[Haut](#top)]

## <a name="examples"></a><a name="examples"></a> Exemples

Pour obtenir des exemples qui utilisent les `send` fonctions et, `asend` `receive` consultez les rubriques suivantes :

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Comment : implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md)

- [Comment : fournir des fonctions de travail aux classes Call et transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md)

- [Comment : utiliser le transformateur dans un pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md)

- [Comment : effectuer une sélection parmi les tâches terminées](../../parallel/concrt/how-to-select-among-completed-tasks.md)

- [Comment : envoyer un message à intervalles réguliers](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md)

- [Comment : utiliser un filtre de bloc de message](../../parallel/concrt/how-to-use-a-message-block-filter.md)

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[send, fonction](reference/concurrency-namespace-functions.md#send)<br/>
[asend, fonction](reference/concurrency-namespace-functions.md#asend)<br/>
[receive, fonction](reference/concurrency-namespace-functions.md#receive)<br/>
[try_receive, fonction](reference/concurrency-namespace-functions.md#try_receive)
