---
title: 'Procédure : Implémenter divers modèles de producteur-consommateur'
ms.date: 11/04/2016
helpviewer_keywords:
- producer-consumer patterns, implementing [Concurrency Runtime]
- implementing producer-consumer patterns [Concurrency Runtime]
ms.assetid: 75f2c7cc-5399-49ea-98eb-847fe6747169
ms.openlocfilehash: 113518e97b6715384b5e7b84b0d0eab63dfcfcc7
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57296278"
---
# <a name="how-to-implement-various-producer-consumer-patterns"></a>Procédure : Implémenter divers modèles de producteur-consommateur

Cette rubrique décrit comment implémenter le modèle de producteur-consommateur dans votre application. Dans ce modèle, le *producteur* envoie des messages à un bloc de message et le *consommateur* lit les messages de ce bloc.

La rubrique illustre deux scénarios. Dans le premier scénario, le consommateur doit recevoir chaque message envoyé par le producteur. Dans le second scénario, le consommateur interroge régulièrement les données et par conséquent ne devra pas recevoir chaque message.

Les deux exemples dans cette rubrique utilisent des agents, les blocs de messages et les fonctions de passage de message pour transmettre les messages du producteur au consommateur. L’agent producteur utilise le [concurrency::send](reference/concurrency-namespace-functions.md#send) fonction pour écrire des messages à un [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md) objet. L’agent de consommateur utilise le [concurrency::receive](reference/concurrency-namespace-functions.md#receive) fonction permettant de lire des messages à partir d’un [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) objet. Les deux agents conservent une valeur de sentinelle pour coordonner la fin du traitement.

Pour plus d’informations sur les agents asynchrones, consultez [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md). Pour plus d’informations sur les blocs de messages et des fonctions de passage de messages, consultez [des blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md) et [fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md).

## <a name="example"></a>Exemple

Dans cet exemple, l’agent producteur envoie une série de nombres à l’agent de consommateur. Le consommateur reçoit chacun de ces nombres et calcule leur moyenne. L’application écrit la moyenne dans la console.

Cet exemple utilise un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objet afin de permettre au producteur de messages de file d’attente. Le `unbounded_buffer` la classe implémente `ITarget` et `ISource` afin que le producteur et le consommateur peuvent envoyer et recevoir des messages vers et depuis une mémoire tampon partagée. Le `send` et `receive` fonctions coordonnent la tâche de propagation des données du producteur au consommateur.

[!code-cpp[concrt-producer-consumer-average#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
The average is 50.
```

## <a name="example"></a>Exemple

Dans cet exemple, l’agent producteur envoie une série de cotations boursières à l’agent de consommateur. L’agent de consommateur lit le devis actuel régulièrement et imprime sur la console.

Cet exemple ressemble au précédent, sauf qu’elle utilise un [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objet afin de permettre le producteur de partager un message avec le consommateur. Comme dans l’exemple précédent, `overwrite_buffer` la classe implémente `ITarget` et `ISource` afin que le producteur et le consommateur peuvent agir sur un tampon de messages partagé.

[!code-cpp[concrt-producer-consumer-quotes#1](../../parallel/concrt/codesnippet/cpp/how-to-implement-various-producer-consumer-patterns_2.cpp)]

Cet exemple produit la sortie suivante.

```Output
Current quote is 24.44.
Current quote is 24.44.
Current quote is 24.65.
Current quote is 24.99.
Current quote is 23.76.
Current quote is 22.30.
Current quote is 25.89.
```

À la différence avec un `unbounded_buffer` objet, le `receive` fonction ne supprime pas le message à partir de la `overwrite_buffer` objet. Si le consommateur lit à partir de la mémoire tampon de message plusieurs fois avant que le producteur remplace ce message, le récepteur Obtient le même message à chaque fois.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `producer-consumer.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc producer-consumer.cpp**

## <a name="see-also"></a>Voir aussi

[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)
