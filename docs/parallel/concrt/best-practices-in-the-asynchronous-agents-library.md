---
title: Meilleures pratiques de la bibliothèque d’Agents asynchrones | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- best practices, Asynchronous Agents Library
- Asynchronous Agents Library, best practices
- Asynchronous Agents Library, practices to avoid
- practices to avoid, Asynchronous Agents Library
ms.assetid: 85f52354-41eb-4b0d-98c5-f7344ee8a8cf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8f1b20342ad6bb64c653a211f9af2fb9e9130286
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692663"
---
# <a name="best-practices-in-the-asynchronous-agents-library"></a>meilleures pratiques pour la bibliothèque d’agents asynchrones
Ce document décrit comment utiliser efficacement la bibliothèque d’Agents asynchrones. La bibliothèque d’Agents promeut un modèle de programmation basé sur acteur et un dans le processus passage des messages de flux de données à granularité grossière et les tâches de traitement « pipeline ».  
  
 Pour plus d’informations sur la bibliothèque d’Agents, consultez [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md).  
  
##  <a name="top"></a> Sections  
 Ce document contient les sections suivantes :  
  
- [Utiliser des Agents pour isoler l’état](#isolation)  
  
- [Utiliser un mécanisme de limitation pour limiter le nombre de Messages dans un Pipeline de données](#throttling)  
  
- [N’effectuez pas de travail de granularité fine dans un Pipeline de données](#fine-grained)  
  
- [Ne passez pas de charges de messages volumineux par valeur](#large-payloads)  
  
- [Utiliser shared_ptr dans un données réseau lorsque la propriété n’est pas défini](#ownership)  
  
##  <a name="isolation"></a> Utiliser des Agents pour isoler l’état  
 La bibliothèque d’Agents fournit des alternatives à l’état partagé en vous permettant de connecter des composants isolés via un mécanisme de passage de messages asynchrone. Agents asynchrones sont plus efficaces lorsqu’ils isolent leur état interne d’autres composants. En l’état est isolé, plusieurs composants ne traitent généralement pas de données partagées. L’isolation d’état peut permettre à votre application à l’échelle, car il réduit la contention de mémoire partagée. L’isolation d’état réduit également la possibilité de conditions de concurrence et de blocage, car les composants n’ont pas synchroniser l’accès aux données partagées.  
  
 En général, vous isolez état dans un agent en maintenant les membres de données dans le `private` ou `protected` sections de la classe de l’agent et à l’aide de mémoires tampons de messages pour communiquer les changements d’état. L’exemple suivant illustre la `basic_agent` (classe), qui dérive de [concurrency::agent](../../parallel/concrt/reference/agent-class.md). La `basic_agent` classe utilise deux mémoires tampons de messages pour communiquer avec les composants externes. Un tampon de messages conserve les messages entrants. l’autre mémoire tampon de messages conserve les messages sortants.  
  
 [!code-cpp[concrt-simple-agent#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_1.cpp)]  
  
 Pour obtenir des exemples complets sur la façon de définir et utiliser des agents, consultez [procédure pas à pas : création d’une Application basée sur l’Agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md) et [procédure pas à pas : création d’un Agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md).  
  
 [[Haut](#top)]  
  
##  <a name="throttling"></a> Utiliser un mécanisme de limitation pour limiter le nombre de Messages dans un Pipeline de données  
 De nombreux types de tampon de messages, tels que [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md), peut contenir un nombre illimité de messages. Lorsqu’un producteur de message envoie des messages à un pipeline de données plus rapidement que le consommateur peut traiter ces messages, l’application peut entrer dans un état d’insuffisance de mémoire ou de mémoire insuffisante. Vous pouvez utiliser un mécanisme de limitation, par exemple, un sémaphore, pour limiter le nombre de messages actifs simultanément dans un pipeline de données.  
  
 L’exemple de base suivant montre comment utiliser un sémaphore pour limiter le nombre de messages dans un pipeline de données. Les données de pipeline utilise la [concurrency::wait](reference/concurrency-namespace-functions.md#wait) (fonction) pour simuler une opération qui prend au moins 100 millisecondes. Étant donné que l’expéditeur génère des messages plus rapidement que le consommateur peut traiter ces messages, cet exemple définit la `semaphore` classe pour permettre à l’application limiter le nombre de messages actifs.  
  
 [!code-cpp[concrt-message-throttling#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_2.cpp)]  
  
 Le `semaphore` objet limite le pipeline à traiter au maximum deux messages en même temps.  
  
 Le producteur dans cet exemple envoie relativement peu de messages au consommateur. Par conséquent, cet exemple ne présente pas une condition de mémoire insuffisante ou de mémoire insuffisante potentielle. Toutefois, ce mécanisme est utile lorsqu’un pipeline de données contient un nombre relativement élevé de messages.  
  
 Pour plus d’informations sur la création de la classe de sémaphore qui est utilisée dans cet exemple, consultez [Comment : utiliser la classe Context pour implémenter un sémaphore coopératif](../../parallel/concrt/how-to-use-the-context-class-to-implement-a-cooperative-semaphore.md).  
  
 [[Haut](#top)]  
  
##  <a name="fine-grained"></a> N’effectuez pas de travail de granularité fine dans un Pipeline de données  
 La bibliothèque d’Agents est très utile lorsque le travail effectué par un pipeline de données est plutôt grossière. Par exemple, un composant d’application peut lire les données à partir d’un fichier ou une connexion réseau et occasionnellement les envoyer à un autre composant. Le protocole utilisé par la bibliothèque d’Agents pour propager des messages provoque le mécanisme de passage de messages à la plus importante que celle des tâche parallèles fournis par le [bibliothèque de modèles parallèles](../../parallel/concrt/parallel-patterns-library-ppl.md) (PPL). Par conséquent, assurez-vous que le travail effectué par un pipeline de données est suffisamment longue pour compenser cette surcharge.  
  
 Même si un pipeline de données est plus efficace lorsque ses tâches sont à granularité grossière, chaque étape du pipeline de données permet d’effectuer des constructions de bibliothèque de modèles parallèles telles que les groupes de tâches et des algorithmes parallèles pour plus affinées travailler. Pour obtenir un exemple d’un réseau de données à granularité grossière qui utilise un parallélisme affiné à chaque étape de traitement, consultez [procédure pas à pas : création d’un réseau de traitement d’Image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Haut](#top)]  
  
##  <a name="large-payloads"></a> Ne passez pas de charges de messages volumineux par valeur  

 Dans certains cas, le runtime crée une copie de chaque message qu’il transmet à partir d’une mémoire tampon des messages à une autre mémoire tampon des messages. Par exemple, le [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) classe offre une copie de chaque message qu’il reçoit à chacune de ses cibles. Le runtime crée également une copie des données du message lorsque vous utilisez les fonctions de passage de messages, tels que [concurrency::send](reference/concurrency-namespace-functions.md#send) et [concurrency::receive](reference/concurrency-namespace-functions.md#receive) pour écrire et lire des messages à partir d’un message mémoire tampon. Bien que ce mécanisme permet d’éliminer le risque d’écrire simultanément aux données partagées, il peut entraîner des performances médiocres de mémoire lors de la charge utile du message est relativement importante.  
  
 Vous pouvez utiliser des pointeurs ou références pour améliorer les performances de la mémoire lorsque vous transmettez des messages qui ont une charge utile importante. L’exemple suivant compare les messages volumineux de passage par valeur au passage de pointeurs vers le même type de message. L’exemple définit deux types d’agents, `producer` et `consumer`, qui agissent sur `message_data` objets. L’exemple compare le temps requis pour le producteur envoie plusieurs `message_data` au consommateur à l’heure qui est requis pour l’agent producteur envoie plusieurs pointeurs vers les objets `message_data` objets au consommateur.  
  
 [!code-cpp[concrt-message-payloads#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_3.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
Using message_data...  
took 437ms.  
Using message_data*...  
took 47ms.  
```  
  
 La version qui utilise des pointeurs est plus performante, car elle élimine le besoin pour le runtime créer une copie complète de chaque `message_data` objet qu’il transmet du producteur au consommateur.  
  
 [[Haut](#top)]  
  
##  <a name="ownership"></a> Utiliser shared_ptr dans un données réseau lorsque la propriété n’est pas défini  
 Lorsque vous envoyez des messages par le pointeur via un pipeline de transmission de messages ou réseau, vous généralement allouez la mémoire pour chaque message à l’avant du réseau et libérez de la mémoire à la fin de réseau. Bien que ce mécanisme fonctionne habituellement correctement, il existe des cas dans lesquels il est difficile ou impossible à l’utiliser. Par exemple, considérez le cas où le réseau de données contient plusieurs nœuds de fin. Dans ce cas, il n’existe aucun emplacement évident pour libérer la mémoire pour les messages.  
  
 Pour résoudre ce problème, vous pouvez utiliser un mécanisme, par exemple, [std::shared_ptr](../../standard-library/shared-ptr-class.md), qui permet à un pointeur qui seront détenus par plusieurs composants. Lors de la dernière `shared_ptr` qui possède une ressource est détruit, la ressource est également libérée.  
  
 L’exemple suivant montre comment utiliser `shared_ptr` pour partager des valeurs de pointeur entre plusieurs mémoires tampons de messages. L’exemple se connecte un [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) objet à trois [concurrency::call](../../parallel/concrt/reference/call-class.md) objets. La `overwrite_buffer` classe offre des messages à chacune de ses cibles. Étant donné que plusieurs propriétaires des données à la fin de réseau, cet exemple utilise `shared_ptr` pour permettre à chaque `call` objet à partager la propriété des messages.  
  
 [!code-cpp[concrt-message-sharing#1](../../parallel/concrt/codesnippet/cpp/best-practices-in-the-asynchronous-agents-library_4.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
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
 [Meilleures pratiques de Runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-best-practices.md)   
 [Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)   
 [Procédure pas à pas : Création d’une Application basée sur l’Agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)   
 [Procédure pas à pas : Création d’un Agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)   
 [Procédure pas à pas : Création d’un réseau de traitement d’Image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md)   
 [Meilleures pratiques de la bibliothèque de modèles parallèles](../../parallel/concrt/best-practices-in-the-parallel-patterns-library.md)   
 [Bonnes pratiques en général du runtime d’accès concurrentiel](../../parallel/concrt/general-best-practices-in-the-concurrency-runtime.md)

