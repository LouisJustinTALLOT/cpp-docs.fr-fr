---
title: 'Comment : implémenter divers modèles de producteur-consommateur'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 70813adf6715a2bcaf4af7370ce43d99c44263bd
ms.sourcegitcommit: 94893973211d0b254c8bcdcf0779997dcc136b0c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91413773"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Comment : implémenter divers modèles de producteur-consommateur

Cette rubrique explique comment implémenter le modèle producteur-consommateur dans votre application. Dans ce modèle, le *producteur* envoie des messages à un bloc de message et le *consommateur* lit les messages de ce bloc.

La rubrique illustre deux scénarios. Dans le premier scénario, le consommateur doit recevoir chaque message envoyé par le producteur. Dans le second scénario, le consommateur interroge périodiquement les données et n’a donc pas besoin de recevoir chaque message.

Les deux exemples de cette rubrique utilisent des agents, des blocs de messages et des fonctions de passage de messages pour transmettre des messages du producteur au consommateur. L’agent producteur utilise la fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) pour écrire des messages dans un objet [Concurrency :: ITarget](../../parallel/concrt/reference/itarget-class.md) . L’agent consommateur utilise la fonction [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) pour lire les messages d’un objet [Concurrency :: ISource](../../parallel/concrt/reference/isource-class.md) . Les deux agents contiennent une valeur de sentinelle pour coordonner la fin du traitement.

Pour plus d’informations sur les agents asynchrones, consultez [agents asynchrones](../../parallel/concrt/asynchronous-agents.md). Pour plus d’informations sur les blocs de messages et les fonctions de transmission de messages, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md) et [fonctions de passage de message](../../parallel/concrt/message-passing-functions.md).

## <a name="example-send-series-of-numbers-to-consumer-agent"></a>Exemple : envoyer des séries de numéros à l’agent du consommateur

Dans cet exemple, l’agent de producteur envoie une série de nombres à l’agent du consommateur. Le consommateur reçoit chacun de ces nombres et calcule leur moyenne. L’application écrit la moyenne sur la console.

Cet exemple utilise un objet [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) pour permettre au producteur de mettre en file d’attente des messages. La `unbounded_buffer` classe implémente `ITarget` et `ISource` afin que le producteur et le consommateur puissent envoyer et recevoir des messages vers et à partir d’une mémoire tampon partagée. Les `send` `receive` fonctions et coordonnent la tâche de propagation des données du producteur au consommateur.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
The average is 50.
```

## <a name="example-send-series-of-stock-quotes-to-consumer-agent"></a>Exemple : envoyer une série de cotations boursières à l’agent Consumer

Dans cet exemple, l’agent de producteur envoie une série de cotations boursières à l’agent du consommateur. L’agent du consommateur lit régulièrement le guillemet en cours et l’imprime sur la console.

Cet exemple ressemble à l’exemple précédent, à ceci près qu’il utilise un objet [Concurrency :: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) pour permettre au producteur de partager un message avec le consommateur. Comme dans l’exemple précédent, `overwrite_buffer` la classe implémente `ITarget` et `ISource` afin que le producteur et le consommateur puissent agir sur une mémoire tampon de messages partagée.

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

Cet exemple produit l’exemple de sortie suivant.

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

Contrairement à un `unbounded_buffer` objet, la `receive` fonction ne supprime pas le message de l' `overwrite_buffer` objet. Si le consommateur lit plus d’une fois le tampon de messages avant que le producteur ne remplace ce message, le destinataire obtient le même message à chaque fois.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `producer-consumer.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe/EHsc Producer-Consumer. cpp**

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)
