---
title: "Procédure pas à pas : création d'un bloc de message personnalisé"
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: 3386994dce68812cf3ed0852a24d8910cb903acf
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81368557"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Procédure pas à pas : création d'un bloc de message personnalisé

Ce document décrit comment créer un type de bloc de messages personnalisé qui commande les messages entrants par priorité.

Bien que les types intégrés de bloc de messages fournissent un large éventail de fonctionnalités, vous pouvez créer votre propre type de bloc de message et le personnaliser pour répondre aux exigences de votre application. Pour une description des types intégrés de bloc de message qui sont fournis par la bibliothèque d’agents asynchrones, voir [asynchrone Messages Blocks](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Prérequis

Lisez les documents suivants avant de commencer cette procédure pas à pas :

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de message](../../parallel/concrt/message-passing-functions.md)

## <a name="sections"></a><a name="top"></a>Sections

Cette procédure pas à pas contient les sections suivantes :

- [Conception d’un bloc de messages personnalisé](#design)

- [Définir la classe priority_buffer](#class)

- [Exemple complet](#complete)

## <a name="designing-a-custom-message-block"></a><a name="design"></a>Conception d’un bloc de messages personnalisé

Les blocs de messages participent à l’envoi et à la réception de messages. Un bloc de messages qui envoie des messages est connu comme un *bloc source*. Un bloc de messages qui reçoit des messages est connu comme un *bloc cible*. Un bloc de message qui envoie et reçoit des messages est connu sous le nom de *bloc de propagateur*. La Bibliothèque des agents utilise la [concurrence](../../parallel/concrt/reference/isource-class.md) de classe abstraite : : ISource pour représenter les blocs sources et la concurrence abstraite de classe [: : ITarget](../../parallel/concrt/reference/itarget-class.md) pour représenter des blocs cibles. Types de bloc de message `ISource`qui agissent comme sources dérivent de ; types de bloc de messages `ITarget`qui agissent comme des cibles dérivent de .

Bien que vous puissiez tirer `ISource` votre `ITarget`type de bloc de message directement à partir et , la bibliothèque des agents définit trois classes de base qui exécutent une grande partie de la fonctionnalité qui est commun à tous les types de bloc de messages, par exemple, la manipulation des erreurs et la connexion des blocs de messages ensemble d’une manière de concurrence sûre. La [concordance::source_block](../../parallel/concrt/reference/source-block-class.md) classe dérive et envoie `ISource` des messages à d’autres blocs. La [concordance::target_block](../../parallel/concrt/reference/target-block-class.md) classe dérive et reçoit `ITarget` des messages d’autres blocs. La [concordance: :propagator-bloc](../../parallel/concrt/reference/propagator-block-class.md) classe dérive et `ISource` `ITarget` envoie des messages à d’autres blocs et il reçoit des messages d’autres blocs. Nous vous recommandons d’utiliser ces trois classes de base pour gérer les détails de l’infrastructure afin que vous puissiez vous concentrer sur le comportement de votre bloc de messages.

Les `source_block` `target_block`, `propagator_block` et les classes sont des modèles qui sont paramétrés sur un type qui gère les connexions, ou des liens, entre les blocs source et cible et sur un type qui gère la façon dont les messages sont traités. La Bibliothèque des agents définit deux types qui effectuent la gestion des liens, [la concordance: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) et [la concurrence::multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). La `single_link_registry` classe permet de rattaillard de la part d’une source ou d’une cible. La `multi_link_registry` classe permet de rattaillard de message lié à plusieurs sources ou à plusieurs cibles. La Bibliothèque des agents définit une classe qui effectue la gestion des messages, [la concordance::ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). La `ordered_message_processor` classe permet aux blocs de messages de traiter les messages dans l’ordre dans lequel il les reçoit.

Pour mieux comprendre comment les blocs de messages se rapportent à leurs sources et cibles, prenons l’exemple suivant. Cet exemple montre la déclaration de la [concordance::classe de transformateur.](../../parallel/concrt/reference/transformer-class.md)

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

La `transformer` classe dérive `propagator_block`de , et agit donc à la fois comme un bloc source et comme un bloc cible. Il accepte les `_Input` messages de type `_Output`et envoie des messages de type . La `transformer` classe spécifie `single_link_registry` en tant `multi_link_registry` que gestionnaire de lien pour tous les blocs cibles et en tant que gestionnaire de lien pour tous les blocs sources. Par conséquent, un `transformer` objet peut avoir jusqu’à une cible et un nombre illimité de sources.

Une classe qui `source_block` dérive de doit mettre en œuvre six méthodes: [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message), et [resume_propagation](reference/source-block-class.md#resume_propagation). Une classe qui `target_block` dérive de doit mettre en œuvre la méthode [propagate_message](reference/propagator-block-class.md#propagate_message) et peut implémenter optionnellement la méthode [send_message.](reference/propagator-block-class.md#send_message) Dérivé de `propagator_block` est fonctionnellement équivalent à dérivé `source_block` `target_block`des deux et .

La `propagate_to_any_targets` méthode est appelée par le temps d’exécution pour traiter asynchronement ou synchronement tous les messages entrants et propager tous les messages sortants. La `accept_message` méthode est appelée par les blocs cibles pour accepter les messages. De nombreux types de `unbounded_buffer`blocs de messages, tels que , envoyer des messages uniquement à la première cible qui le recevrait. Par conséquent, il transfère la propriété du message à la cible. D’autres types de blocs de messages, tels que [la concurrence::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), offrent des messages à chacun de ses blocs cibles. Par `overwrite_buffer` conséquent, crée une copie du message pour chacune de ses cibles.

Les `reserve_message` `consume_message`, `release_message`, `resume_propagation` et les méthodes permettent aux blocs de messages de participer à la réservation de messages. Les blocs `reserve_message` cibles appellent la méthode lorsqu’on leur offre un message et doivent réserver le message pour une utilisation ultérieure. Une fois qu’un bloc cible `consume_message` réserve un message, `release_message` il peut appeler la méthode pour consommer ce message ou la méthode pour annuler la réservation. Comme avec `accept_message` la méthode, `consume_message` la mise en œuvre de peut soit transférer la propriété du message ou retourner une copie du message. Après qu’un bloc cible consomme ou libère un `resume_propagation` message réservé, l’heure d’exécution appelle la méthode. Typiquement, cette méthode continue la propagation du message, en commençant par le message suivant dans la file d’attente.

Le temps d’exécution appelle la `propagate_message` méthode pour transférer asynchronement un message d’un autre bloc à l’actuel. La `send_message` méthode `propagate_message`ressemble, sauf qu’elle synchrone, au lieu de l’asynchrone, envoie le message aux blocs cibles. La mise `send_message` en œuvre par défaut de rejette tous les messages entrants. Le temps d’exécution n’appelle aucune de ces méthodes si le message ne passe pas la fonction de filtre optionnelle qui est associée au bloc cible. Pour plus d’informations sur les filtres de message, voir [Asynchrone Messages Blocks](../../parallel/concrt/asynchronous-message-blocks.md).

[[Top](#top)]

## <a name="defining-the-priority_buffer-class"></a><a name="class"></a>Définir la classe priority_buffer

La `priority_buffer` classe est un type de bloc de messages personnalisé qui commande les messages entrants d’abord par priorité, puis par l’ordre dans lequel les messages sont reçus. La `priority_buffer` classe ressemble à la [concurrence: :unbounded_buffer](reference/unbounded-buffer-class.md) classe parce qu’il détient une file d’attente de messages, et aussi parce qu’il agit à la fois comme une source et un bloc de message cible et peut avoir à la fois plusieurs sources et plusieurs cibles. Toutefois, `unbounded_buffer` la propagation du message ne fonde que sur l’ordre dans lequel il reçoit des messages de ses sources.

La `priority_buffer` classe reçoit des messages de type `PriorityType` std::[tuple](../../standard-library/tuple-class.md) qui contiennent et `Type` les éléments. `PriorityType`se réfère au type qui détient la priorité de chaque message; `Type` se réfère à la partie données du message. La `priority_buffer` classe envoie `Type`des messages de type . La `priority_buffer` classe gère également deux files d’attente de messages : un objet [de file d’attente de :priority](../../standard-library/priority-queue-class.md) pour les messages entrants et un std : objet[de file d’attente](../../standard-library/queue-class.md) pour les messages sortants. Commander des messages par priorité `priority_buffer` est utile lorsqu’un objet reçoit plusieurs messages simultanément ou lorsqu’il reçoit plusieurs messages avant que les messages ne soient lus par les consommateurs.

En plus des sept méthodes qu’une `propagator_block` classe qui `priority_buffer` dérive de doit `link_target_notification` `send_message` mettre en œuvre, la classe l’emporte également sur les méthodes et les méthodes. La `priority_buffer` classe définit également deux méthodes `enqueue` `dequeue`d’aide publique, et `propagate_priority_order`, et une méthode d’aide privée, .

La procédure suivante décrit comment `priority_buffer` mettre en œuvre la classe.

#### <a name="to-define-the-priority_buffer-class"></a>Définir la classe priority_buffer

1. Créez un fichier d’en-tête CMD et nommez-le `priority_buffer.h`. Alternativement, vous pouvez utiliser un fichier d’en-tête existant qui fait partie de votre projet.

1. Dans `priority_buffer.h`, ajouter le code suivant.

    [!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. Dans `std` l’espace de nom, définissez les spécialisations de [std::less](../../standard-library/less-struct.md) et [std::plus grand](../../standard-library/greater-struct.md) qui agissent sur la concurrence:: objets[de message.](../../parallel/concrt/reference/message-class.md)

    [!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   La `priority_buffer` classe `message` stocke `priority_queue` des objets dans un objet. Ces spécialisations de type permettent à la file d’attente prioritaire de trier les messages en fonction de leur priorité. La priorité est le `tuple` premier élément de l’objet.

1. Dans `concurrencyex` l’espace nom, déclarez la `priority_buffer` classe.

    [!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   La classe `priority_buffer` dérive de la classe `propagator_block`. Par conséquent, il peut à la fois envoyer et recevoir des messages. La `priority_buffer` classe peut avoir plusieurs cibles `Type`qui reçoivent des messages de type . Il peut également avoir plusieurs sources `tuple<PriorityType, Type>`qui envoient des messages de type .

1. Dans `private` la section `priority_buffer` de la classe, ajoutez les variables des membres suivantes.

    [!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   L’objet `priority_queue` contient des messages entrants; l’objet `queue` contient des messages sortants. Un `priority_buffer` objet peut recevoir plusieurs messages simultanément; l’objet `critical_section` synchronise l’accès à la file d’attente des messages d’entrée.

1. Dans `private` la section, définissez le constructeur de copie et l’opérateur d’affectation. Cela empêche `priority_queue` les objets d’être assignables.

    [!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. Dans `public` la section, définissez les constructeurs qui sont communs à de nombreux types de blocs de messages. Définissez également le destructeur.

    [!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. Dans `public` la section, `enqueue` définir `dequeue`les méthodes et . Ces méthodes d’aide fournissent une autre façon d’envoyer des messages et de recevoir des messages d’un `priority_buffer` objet.

    [!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

1. Dans `protected` la section, `propagate_to_any_targets` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   La `propagate_to_any_targets` méthode transfère le message qui se trouve à l’avant de la file d’attente d’entrée à la file d’attente de sortie et propage tous les messages dans la file d’attente de sortie.

1. Dans `protected` la section, `accept_message` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Lorsqu’un bloc `accept_message` cible appelle `priority_buffer` la méthode, la classe transfère la propriété du message au premier bloc cible qui l’accepte. (Cela ressemble au `unbounded_buffer`comportement de .)

1. Dans `protected` la section, `reserve_message` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   La `priority_buffer` classe permet à un bloc cible de réserver un message lorsque l’identifiant de message fourni correspond à l’identifiant du message qui se trouve à l’avant de la file d’attente. En d’autres termes, une cible `priority_buffer` peut réserver le message si l’objet n’a pas encore reçu de message supplémentaire et n’a pas encore propagé le message actuel.

1. Dans `protected` la section, `consume_message` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Un bloc `consume_message` cible appelle à transférer la propriété du message qu’il a réservé.

1. Dans `protected` la section, `release_message` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Un bloc `release_message` cible appelle pour annuler sa réservation à un message.

1. Dans `protected` la section, `resume_propagation` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Le temps `resume_propagation` d’exécution appelle après qu’un bloc cible consomme ou libère un message réservé. Cette méthode propage tous les messages qui sont dans la file d’attente de sortie.

1. Dans `protected` la section, `link_target_notification` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   La `_M_pReservedFor` variable du membre est `source_block`définie par la classe de base, . Cette variable de membre indique le bloc cible, le cas échéant, qui tient une réservation au message qui se trouve à l’avant de la file d’attente de sortie. Le temps `link_target_notification` d’exécution s’appelle `priority_buffer` lorsqu’une nouvelle cible est liée à l’objet. Cette méthode propage tous les messages qui sont dans la file d’attente de sortie si aucune cible ne détient une réservation.

1. Dans `private` la section, `propagate_priority_order` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Cette méthode propage tous les messages de la file d’attente de sortie. Chaque message dans la file d’attente est offert à chaque bloc cible jusqu’à ce que l’un des blocs cibles accepte le message. La `priority_buffer` classe conserve l’ordre des messages sortants. Par conséquent, le premier message dans la file d’attente de sortie doit être accepté par un bloc cible avant que cette méthode offre tout autre message aux blocs cibles.

1. Dans `protected` la section, `propagate_message` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   La `propagate_message` méthode `priority_buffer` permet à la classe d’agir comme un récepteur de message, ou de cibler. Cette méthode reçoit le message qui est offert par le bloc source fournie et insère ce message dans la file d’attente prioritaire. La `propagate_message` méthode envoie alors asynchronement tous les messages de sortie aux blocs cibles.

   Le temps d’exécution appelle cette méthode lorsque vous appelez la [concurrence::asend](reference/concurrency-namespace-functions.md#asend) fonction ou lorsque le bloc de message est connecté à d’autres blocs de messages.

1. Dans `protected` la section, `send_message` définissez la méthode.

    [!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   La `send_message` méthode `propagate_message`ressemble . Cependant, il envoie les messages de sortie synchronement au lieu de asynchrone.

   Le temps d’exécution appelle cette méthode au cours d’une opération d’envoi synchrone, comme lorsque vous appelez la [concordance::envoyer](reference/concurrency-namespace-functions.md#send) la fonction.

La `priority_buffer` classe contient des surcharges de constructeurs qui sont typiques dans de nombreux types de blocs de messages. Certaines surcharges de constructeurs prennent [la concurrence ::Scheduler](../../parallel/concrt/reference/scheduler-class.md) ou [concordance::ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) objets, qui permettent au bloc de message d’être géré par un planificateur de tâches spécifique. D’autres surcharges de constructeurs prennent une fonction de filtre. Les fonctions de filtre permettent aux blocs de messages d’accepter ou de rejeter un message sur la base de sa charge utile. Pour plus d’informations sur les filtres de message, voir [Asynchrone Messages Blocks](../../parallel/concrt/asynchronous-message-blocks.md). Pour plus d’informations sur les planificateurs de tâches, voir [Task Scheduler](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Parce `priority_buffer` que la classe commande des messages par priorité, puis par l’ordre dans lequel les messages sont reçus, cette classe est plus utile quand il reçoit des messages asynchronement, par exemple, lorsque vous appelez la [concordance::fonction d’urgence](reference/concurrency-namespace-functions.md#asend) ou lorsque le bloc de message est connecté à d’autres blocs de messages.

[[Top](#top)]

## <a name="the-complete-example"></a><a name="complete"></a>L’exemple complet

L’exemple suivant montre la `priority_buffer` définition complète de la classe.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

L’exemple suivant effectue simultanément `asend` un certain nombre de personnes et [une concordance : recevez des](reference/concurrency-namespace-functions.md#receive) opérations sur un `priority_buffer` objet.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Cet exemple produit la sortie de l’échantillon suivant.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

La `priority_buffer` classe commande des messages d’abord par priorité, puis par l’ordre dans lequel il reçoit des messages. Dans cet exemple, des messages ayant une plus grande priorité numérique sont insérés vers l’avant de la file d’attente.

[[Top](#top)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un `priority_buffer` projet Visual Studio, `priority_buffer.h` ou collez la définition `priority_buffer.cpp` de la classe dans un fichier qui est nommé et le programme de test dans un fichier qui est nommé, puis exécutez la commande suivante dans une fenêtre de commande de studio visuel prompt.

**cl.exe /EHsc priority_buffer.cpp**

## <a name="see-also"></a>Voir aussi

[Procédure pas à pas De Concurrency Runtime](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de message](../../parallel/concrt/message-passing-functions.md)
