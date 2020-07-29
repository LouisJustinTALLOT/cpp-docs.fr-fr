---
title: meilleures pratiques pour la bibliothèque d’agents asynchrones
ms.date: 11/04/2016
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
ms.openlocfilehash: 99780de11d85831a6901f370d2491f15ef88c0b1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231739"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>meilleures pratiques pour la bibliothèque d’agents asynchrones

Ce document explique comment utiliser efficacement la bibliothèque des agents asynchrones. La bibliothèque d’agents promeut un modèle de programmation basé sur les acteurs et le passage de messages in-process pour les tâches de flux de données à granularité grossière et de traitement pipeline.

Pour plus d’informations sur la bibliothèque d’agents, consultez [Asynchronous agents Library](../../parallel/concrt/asynchronous-agents-library.md).

## <a name="sections"></a><a name="top"></a>Sections

Ce document contient les sections suivantes :

- [Utiliser des agents pour isoler l’État](#isolation)

- [Utiliser un mécanisme de limitation pour limiter le nombre de messages dans un pipeline de données](#throttling)

- [N’effectuez pas de travail affiné dans un pipeline de données](#fine-grained)

- [Ne pas passer les charges utiles de messages volumineux par valeur](#large-payloads)

- [Utiliser shared_ptr dans un réseau de données lorsque la propriété n’est pas définie](#ownership)

## <a name="use-agents-to-isolate-state"></a><a name="isolation"></a>Utiliser des agents pour isoler l’État

La bibliothèque d’agents fournit des alternatives à l’état partagé en vous permettant de connecter des composants isolés par le biais d’un mécanisme de transmission de messages asynchrone. Les agents asynchrones sont plus efficaces lorsqu’ils isolent leur état interne des autres composants. En isolant l’État, plusieurs composants n’agissent généralement pas sur des données partagées. L’isolation d’État peut permettre à votre application de se mettre à l’échelle, car elle réduit la contention de mémoire partagée. L’isolation d’État réduit également le risque d’interblocage et de conditions de concurrence critique, car les composants n’ont pas besoin de synchroniser l’accès aux données partagées.

En général, vous isolez l’état d’un agent en contenant les données membres dans les **`private`** **`protected`** sections ou de la classe de l’agent et en utilisant des tampons de messages pour communiquer les modifications d’État. L’exemple suivant illustre la `basic_agent` classe, qui dérive de [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md). La `basic_agent` classe utilise deux mémoires tampons de messages pour communiquer avec les composants externes. Une mémoire tampon de messages contient des messages entrants ; l’autre mémoire tampon de messages contient des messages sortants.

[!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]

Pour obtenir des exemples complets sur la façon de définir et d’utiliser des agents, consultez [procédure pas à pas : création d’une application basée sur un agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) et [procédure pas à pas : création d’un agent de flux](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)de données.

[[Haut](#top)]

## <a name="use-a-throttling-mechanism-to-limit-the-number-of-messages-in-a-data-pipeline"></a><a name="throttling"></a>Utiliser un mécanisme de limitation pour limiter le nombre de messages dans un pipeline de données

De nombreux types de tampons de messages, tels que [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md), peuvent contenir un nombre illimité de messages. Lorsqu’un producteur de message envoie des messages à un pipeline de données plus rapidement que le consommateur ne peut traiter ces messages, l’application peut entrer dans un état de mémoire insuffisante ou de mémoire insuffisante. Vous pouvez utiliser un mécanisme de limitation, par exemple un sémaphore, pour limiter le nombre de messages qui sont actifs simultanément dans un pipeline de données.

L’exemple de base suivant montre comment utiliser un sémaphore pour limiter le nombre de messages dans un pipeline de données. Le pipeline de données utilise la fonction [Concurrency :: wait](reference/concurrency-namespace-functions.md#wait) pour simuler une opération qui prend au moins 100 millisecondes. Étant donné que l’expéditeur génère des messages plus rapidement que le consommateur ne peut traiter ces messages, cet exemple définit la `semaphore` classe pour permettre à l’application de limiter le nombre de messages actifs.

[!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]

L' `semaphore` objet limite le pipeline pour traiter au plus deux messages en même temps.

Dans cet exemple, le producteur envoie relativement peu de messages au consommateur. Par conséquent, cet exemple ne montre pas une condition de mémoire insuffisante ou de mémoire insuffisante. Toutefois, ce mécanisme est utile lorsqu’un pipeline de données contient un nombre relativement élevé de messages.

Pour plus d’informations sur la création de la classe Semaphore utilisée dans cet exemple, consultez [Comment : utiliser la classe Context pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).

[[Haut](#top)]

## <a name="do-not-perform-fine-grained-work-in-a-data-pipeline"></a><a name="fine-grained"></a>N’effectuez pas de travail affiné dans un pipeline de données

La bibliothèque d’agents est particulièrement utile lorsque le travail effectué par un pipeline de données est relativement grossier. Par exemple, un composant d’application peut lire des données à partir d’un fichier ou d’une connexion réseau et envoyer occasionnellement ces données à un autre composant. Le protocole que la bibliothèque d’agents utilise pour propager les messages entraîne une surcharge du mécanisme de passage de message par rapport aux constructions parallèles de tâche fournies par la [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Par conséquent, assurez-vous que le travail effectué par un pipeline de données est suffisamment long pour compenser cette surcharge.

Bien qu’un pipeline de données soit plus efficace lorsque ses tâches sont grossièrement granuleuses, chaque étape du pipeline de données peut utiliser des constructions PPL, telles que des groupes de tâches et des algorithmes parallèles, pour effectuer des tâches plus précises. Pour obtenir un exemple de réseau de données à granularité grossière qui utilise le parallélisme affiné à chaque étape de traitement, consultez [procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Haut](#top)]

## <a name="do-not-pass-large-message-payloads-by-value"></a><a name="large-payloads"></a>Ne pas passer les charges utiles de messages volumineux par valeur

Dans certains cas, le runtime crée une copie de chaque message qu’il transmet d’une mémoire tampon de messages à une autre mémoire tampon de messages. Par exemple, la classe [Concurrency :: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) offre une copie de chaque message qu’elle reçoit à chacune de ses cibles. Le runtime crée également une copie des données du message lorsque vous utilisez des fonctions de passage de messages telles que [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) et [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) pour écrire des messages dans une mémoire tampon de messages et les lire. Bien que ce mécanisme permette d’éliminer le risque d’écriture simultanée sur des données partagées, cela peut entraîner des performances de mémoire médiocres lorsque la charge utile de message est relativement importante.

Vous pouvez utiliser des pointeurs ou des références pour améliorer les performances de la mémoire lorsque vous transmettez des messages qui ont une charge utile importante. L’exemple suivant compare le passage de messages volumineux par valeur à la transmission de pointeurs vers le même type de message. L’exemple définit deux types d’agents, `producer` et `consumer` , qui agissent sur les `message_data` objets. L’exemple compare le temps nécessaire pour que le producteur envoie plusieurs `message_data` objets au consommateur au moment nécessaire à l’agent producteur pour envoyer plusieurs pointeurs vers des `message_data` objets au consommateur.

[!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]

Cet exemple produit l’exemple de sortie suivant :

```Output
Using message_data...
took 437ms.
Using message_data*...
took 47ms.
```

La version qui utilise des pointeurs est plus efficace, car elle élimine la nécessité pour le runtime de créer une copie complète de chaque `message_data` objet qu’il transmet du producteur au consommateur.

[[Haut](#top)]

## <a name="use-shared_ptr-in-a-data-network-when-ownership-is-undefined"></a><a name="ownership"></a>Utiliser shared_ptr dans un réseau de données lorsque la propriété n’est pas définie

Lorsque vous envoyez des messages par pointeur via un pipeline ou un réseau de transmission de messages, vous allouez généralement la mémoire pour chaque message à l’avant du réseau et libère cette mémoire à la fin du réseau. Bien que ce mécanisme fonctionne souvent bien, il y a des cas où il est difficile, voire impossible, de l’utiliser. Par exemple, considérez le cas dans lequel le réseau de données contient plusieurs nœuds de fin. Dans ce cas, il n’y a pas d’emplacement clair pour libérer la mémoire pour les messages.

Pour résoudre ce problème, vous pouvez utiliser un mécanisme, par exemple [std :: shared_ptr](../../standard-library/shared-ptr-class.md), qui permet à un pointeur d’appartenir à plusieurs composants. Lorsque le dernier `shared_ptr` objet qui possède une ressource est détruit, la ressource est également libérée.

L’exemple suivant montre comment utiliser `shared_ptr` pour partager des valeurs de pointeur entre plusieurs mémoires tampons de messages. L’exemple connecte un objet [Concurrency :: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) à trois objets [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) . La `overwrite_buffer` classe offre des messages à chacune de ses cibles. Comme il existe plusieurs propriétaires de données à la fin du réseau de données, cet exemple utilise `shared_ptr` pour permettre à chaque `call` objet de partager la propriété des messages.

[!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]

Cet exemple produit l’exemple de sortie suivant :

```Output
Creating resource 42...
receiver1: received resource 42
Creating resource 64...
receiver2: received resource 42
receiver1: received resource 64
Destroying resource 42...
receiver2: received resource 64
Destroying resource 64...
```

## <a name="see-also"></a>Voir aussi

[Meilleures pratiques en matière de runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-best-practices.md)<br/>
[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Procédure pas à pas : création d’une application basée sur un agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)<br/>
[Procédure pas à pas : création d’un agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)<br/>
[Procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)<br/>
[Meilleures pratiques dans la bibliothèque de modèles parallèles](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)<br/>
[Meilleures pratiques générales dans le runtime d’accès concurrentiel](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)
