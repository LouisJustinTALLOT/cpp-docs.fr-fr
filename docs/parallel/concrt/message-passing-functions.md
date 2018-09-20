---
title: Fonctions de passage de message | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message passing functions
ms.assetid: 42477c9e-a8a6-4dc4-a98e-93c6dc8c4dd0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b0b7a7afb25d46fa3b521353c4577fbed66e69fd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46436986"
---
# <a name="message-passing-functions"></a>Fonctions de passage de messages

La bibliothèque d’Agents asynchrones fournit plusieurs fonctions qui vous permettent de transmettre des messages entre composants.

Ces fonctions de transmission de messages sont utilisées avec les différents types de blocs de messages. Pour plus d’informations sur les types de blocs de messages qui sont définies par le Runtime d’accès concurrentiel, consultez [des blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

##  <a name="top"></a> Sections

Cette rubrique décrit les fonctions de passage de messages suivantes :

- [envoi et asend](#send)

- [recevoir et try_receive](#receive)

- [Exemples](#examples)

##  <a name="send"></a> envoi et asend

Le [concurrency::send](reference/concurrency-namespace-functions.md#send) fonction envoie un message à la cible spécifiée de façon synchrone et le [concurrency::asend](reference/concurrency-namespace-functions.md#asend) fonction envoie un message à la cible spécifiée de manière asynchrone. À la fois le `send` et `asend` fonctions patienter jusqu'à ce que la cible indique qu’il accepte ou refuse le message.

Le `send` fonction attend jusqu'à ce que la cible accepte ou refuse le message avant de retourner. Le `send` fonction renvoie `true` si le message a été remis et `false` dans le cas contraire. Étant donné que le `send` fonction fonctionne de façon synchrone, le `send` fonction attend que la cible recevoir le message avant de retourner.

À l’inverse, le `asend` fonction n’attend pas que la cible accepte ou refuse le message avant de retourner. Au lieu de cela, le `asend` fonction renvoie `true` si la cible accepte le message et prendra par la suite. Sinon, `asend` retourne `false` pour indiquer que la cible a refusé le message ou différé la décision sur la nécessité de prendre le message.

[[Haut](#top)]

##  <a name="receive"></a> recevoir et try_receive

Le [concurrency::receive](reference/concurrency-namespace-functions.md#receive) et [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive) fonctions lisent les données d’une source donnée. Le `receive` fonction attend des données deviennent disponibles, tandis que le `try_receive` fonction retourne immédiatement.

Utilisez le `receive` fonctionner lorsque vous devez avoir les données pour continuer. Utilisez le `try_receive` fonctionner si vous ne devez pas bloquer le contexte actuel ou si vous n’avez pas à utiliser les données pour continuer.

[[Haut](#top)]

##  <a name="examples"></a> Exemples

Pour obtenir des exemples qui utilisent la `send` et `asend`, et `receive` fonctions, consultez les rubriques suivantes :

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
[try_receive, fonction](reference/concurrency-namespace-functions.md#try_receive)

