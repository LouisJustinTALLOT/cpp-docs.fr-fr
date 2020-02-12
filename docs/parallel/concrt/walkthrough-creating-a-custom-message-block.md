---
title: "Procédure pas à pas : création d'un bloc de message personnalisé"
ms.date: 04/25/2019
helpviewer_keywords:
- creating custom message blocks Concurrency Runtime]
- custom message blocks, creating [Concurrency Runtime]
ms.assetid: 4c6477ad-613c-4cac-8e94-2c9e63cd43a1
ms.openlocfilehash: a29ed382d67b91443bd13e029af2a37c42ee834d
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142828"
---
# <a name="walkthrough-creating-a-custom-message-block"></a>Procédure pas à pas : création d'un bloc de message personnalisé

Ce document décrit comment créer un type de bloc de message personnalisé qui classe les messages entrants par priorité.

Bien que les types de blocs de messages intégrés fournissent un large éventail de fonctionnalités, vous pouvez créer votre propre type de bloc de message et le personnaliser pour répondre aux besoins de votre application. Pour obtenir une description des types de blocs de messages intégrés fournis par la bibliothèque d’agents asynchrones, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

## <a name="prerequisites"></a>Conditions préalables requises

Lisez les documents suivants avant de commencer cette procédure pas à pas :

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

## <a name="top"></a> Sections

Cette procédure pas à pas contient les sections suivantes :

- [Conception d’un bloc de message personnalisé](#design)

- [Définition de la classe priority_buffer](#class)

- [Exemple complet](#complete)

## <a name="design"></a>Conception d’un bloc de message personnalisé

Les blocs de messages participent à l’envoi et à la réception de messages. Un bloc de message qui envoie des messages est appelé un *bloc source*. Un bloc de message qui reçoit des messages est appelé un *bloc cible*. Un bloc de message qui envoie et reçoit des messages est connu sous le nom de *bloc propagateur*. La bibliothèque d’agents utilise la classe abstraite [Concurrency :: ISource](../../parallel/concrt/reference/isource-class.md) pour représenter des blocs sources et la classe abstraite [Concurrency :: ITarget](../../parallel/concrt/reference/itarget-class.md) pour représenter des blocs cibles. Les types de blocs de messages qui agissent en tant que sources dérivent de `ISource`; les types de blocs de messages qui agissent en tant que cibles dérivent de `ITarget`.

Bien que vous puissiez dériver votre type de bloc de message directement à partir de `ISource` et `ITarget`, la bibliothèque d’agents définit trois classes de base qui exécutent la plupart des fonctionnalités communes à tous les types de blocs de message, par exemple, la gestion des erreurs et la connexion des blocs de message de manière simultanée. La classe [Concurrency :: source_block](../../parallel/concrt/reference/source-block-class.md) dérive de `ISource` et envoie des messages à d’autres blocs. La classe [Concurrency :: target_block](../../parallel/concrt/reference/target-block-class.md) dérive de `ITarget` et reçoit des messages d’autres blocs. La classe [Concurrency ::p ropagator_block](../../parallel/concrt/reference/propagator-block-class.md) dérive de `ISource` et `ITarget`, envoie des messages à d’autres blocs et reçoit des messages d’autres blocs. Nous vous recommandons d’utiliser ces trois classes de base pour gérer les détails de l’infrastructure afin que vous puissiez vous concentrer sur le comportement de votre bloc de message.

Les classes `source_block`, `target_block`et `propagator_block` sont des modèles paramétrables sur un type qui gère les connexions, ou liens, entre les blocs source et cible et sur un type qui gère la manière dont les messages sont traités. La bibliothèque d’agents définit deux types qui effectuent la gestion des liens, l' [accès concurrentiel :: single_link_registry](../../parallel/concrt/reference/single-link-registry-class.md) et l' [accès concurrentiel :: multi_link_registry](../../parallel/concrt/reference/multi-link-registry-class.md). La classe `single_link_registry` permet à un bloc de message d’être lié à une source ou à une cible. La classe `multi_link_registry` permet à un bloc de message d’être lié à plusieurs sources ou plusieurs cibles. La bibliothèque d’agents définit une classe qui effectue la gestion des messages, [Concurrency :: ordered_message_processor](../../parallel/concrt/reference/ordered-message-processor-class.md). La classe `ordered_message_processor` permet aux blocs de messages de traiter les messages dans l’ordre dans lequel ils les reçoivent.

Pour mieux comprendre le lien entre les blocs de messages et leurs sources et cibles, examinez l’exemple suivant. Cet exemple illustre la déclaration de la classe [Concurrency :: transformer](../../parallel/concrt/reference/transformer-class.md) .

[!code-cpp[concrt-priority-buffer#20](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_1.cpp)]

La classe `transformer` dérive de `propagator_block`et agit donc à la fois comme un bloc source et comme un bloc cible. Il accepte des messages de type `_Input` et envoie des messages de type `_Output`. La classe `transformer` spécifie `single_link_registry` comme gestionnaire de liens pour tous les blocs cibles et `multi_link_registry` comme gestionnaire de liens pour tous les blocs sources. Par conséquent, un objet `transformer` peut avoir jusqu’à une cible et un nombre illimité de sources.

Une classe qui dérive de `source_block` doit implémenter six méthodes : [propagate_to_any_targets](reference/source-block-class.md#propagate_to_any_targets), [accept_message](reference/source-block-class.md#accept_message), [reserve_message](reference/source-block-class.md#reserve_message), [consume_message](reference/source-block-class.md#consume_message), [release_message](reference/source-block-class.md#release_message)et [resume_propagation](reference/source-block-class.md#resume_propagation). Une classe qui dérive de `target_block` doit implémenter la méthode [propagate_message](reference/propagator-block-class.md#propagate_message) et peut éventuellement implémenter la méthode [send_message](reference/propagator-block-class.md#send_message) . La dérivation à partir de `propagator_block` est fonctionnellement équivalente à la dérivation à partir de `source_block` et de `target_block`.

La méthode `propagate_to_any_targets` est appelée par le runtime pour traiter de façon asynchrone ou synchrone tous les messages entrants et propager les messages sortants. La méthode `accept_message` est appelée par les blocs cibles pour accepter des messages. De nombreux types de bloc de message, tels que `unbounded_buffer`, envoient des messages uniquement à la première cible qui les recevrait. Par conséquent, il transfère la propriété du message à la cible. D’autres types de bloc de message, tels que [Concurrency :: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md), proposent des messages à chacun de ses blocs cibles. Par conséquent, `overwrite_buffer` crée une copie du message pour chacune de ses cibles.

Les méthodes `reserve_message`, `consume_message`, `release_message`et `resume_propagation` permettent aux blocs de messages de participer à la réservation des messages. Les blocs cibles appellent la méthode `reserve_message` lorsqu’ils ont proposé un message et doivent réserver le message pour une utilisation ultérieure. Une fois qu’un bloc cible a réservé un message, il peut appeler la méthode `consume_message` pour utiliser ce message ou la méthode `release_message` pour annuler la réservation. Comme avec la méthode `accept_message`, l’implémentation de `consume_message` peut transférer la propriété du message ou retourner une copie du message. Une fois qu’un bloc cible a consommé ou libéré un message réservé, le runtime appelle la méthode `resume_propagation`. En règle générale, cette méthode continue la propagation des messages, en commençant par le message suivant dans la file d’attente.

Le runtime appelle la méthode `propagate_message` pour transférer de façon asynchrone un message d’un autre bloc à l’objet actuel. La méthode `send_message` ressemble à `propagate_message`, à ceci près qu’elle envoie le message aux blocs cibles de façon synchrone, et non de manière asynchrone. L’implémentation par défaut de `send_message` rejette tous les messages entrants. Le runtime n’appelle aucune de ces méthodes si le message ne passe pas la fonction de filtre facultative associée au bloc cible. Pour plus d’informations sur les filtres de messages, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

[[Haut](#top)]

## <a name="class"></a>Définition de la classe priority_buffer

La classe `priority_buffer` est un type de bloc de message personnalisé qui classe les messages entrants par priorité, puis l’ordre dans lequel les messages sont reçus. La classe `priority_buffer` ressemble à la classe [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) , car elle contient une file d’attente de messages, et elle agit à la fois comme un bloc de message source et cible et peut avoir plusieurs sources et plusieurs cibles. Toutefois, `unbounded_buffer` base la propagation des messages uniquement dans l’ordre dans lequel elle reçoit des messages de ses sources.

La classe `priority_buffer` reçoit des messages de type std ::[Tuple](../../standard-library/tuple-class.md) qui contiennent des éléments `PriorityType` et `Type`. `PriorityType` fait référence au type qui contient la priorité de chaque message ; `Type` fait référence à la partie données du message. La classe `priority_buffer` envoie des messages de type `Type`. La classe `priority_buffer` gère également deux files d’attente de messages : un objet [std ::p riority_queue](../../standard-library/priority-queue-class.md) pour les messages entrants et un objet std ::[queue](../../standard-library/queue-class.md) pour les messages sortants. Le classement des messages par priorité est utile lorsqu’un objet `priority_buffer` reçoit plusieurs messages simultanément ou lorsqu’il reçoit plusieurs messages avant que des messages ne soient lus par les consommateurs.

Outre les sept méthodes qu’une classe qui dérive de `propagator_block` doit implémenter, la classe `priority_buffer` substitue également les méthodes `link_target_notification` et `send_message`. La classe `priority_buffer` définit également deux méthodes d’assistance publiques, `enqueue` et `dequeue`, ainsi qu’une méthode d’assistance privée, `propagate_priority_order`.

La procédure suivante décrit comment implémenter la classe `priority_buffer`.

#### <a name="to-define-the-priority_buffer-class"></a>Pour définir la classe priority_buffer

1. Créez un C++ fichier d’en-tête et nommez-le `priority_buffer.h`. Vous pouvez également utiliser un fichier d’en-tête existant qui fait partie de votre projet.

1. Dans `priority_buffer.h`, ajoutez le code suivant.

[!code-cpp[concrt-priority-buffer#1](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_2.h)]

1. Dans l’espace de noms `std`, définissez les spécialisations de [std :: less](../../standard-library/less-struct.md) et [std :: plus](../../standard-library/greater-struct.md) qui agissent sur les objets Concurrency ::[message](../../parallel/concrt/reference/message-class.md) .

[!code-cpp[concrt-priority-buffer#2](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_3.h)]

   La classe `priority_buffer` stocke des objets `message` dans un objet `priority_queue`. Ces spécialisations de type permettent à la file d’attente de priorité de trier les messages en fonction de leur priorité. La priorité est le premier élément de l’objet `tuple`.

1. Dans l’espace de noms `concurrencyex`, déclarez la classe `priority_buffer`.

[!code-cpp[concrt-priority-buffer#3](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_4.h)]

   La classe `priority_buffer` dérive de la classe `propagator_block`. Par conséquent, il peut envoyer et recevoir des messages. La classe `priority_buffer` peut avoir plusieurs cibles qui reçoivent des messages de type `Type`. Il peut également avoir plusieurs sources qui envoient des messages de type `tuple<PriorityType, Type>`.

1. Dans la section `private` de la classe `priority_buffer`, ajoutez les variables membres suivantes.

[!code-cpp[concrt-priority-buffer#6](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_5.h)]

   L’objet `priority_queue` contient les messages entrants ; l’objet `queue` contient les messages sortants. Un objet `priority_buffer` peut recevoir plusieurs messages simultanément. l’objet `critical_section` synchronise l’accès à la file d’attente des messages d’entrée.

1. Dans la section `private`, définissez le constructeur de copie et l’opérateur d’assignation. Cela empêche l’assignation d’objets `priority_queue`.

[!code-cpp[concrt-priority-buffer#7](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_6.h)]

1. Dans la section `public`, définissez les constructeurs qui sont communs à de nombreux types de blocs de message. Définissez également le destructeur.

[!code-cpp[concrt-priority-buffer#4](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_7.h)]

1. Dans la section `public`, définissez les méthodes `enqueue` et `dequeue`. Ces méthodes d’assistance offrent un autre moyen d’envoyer des messages à un objet `priority_buffer` et de recevoir des messages de celui-ci.

[!code-cpp[concrt-priority-buffer#5](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_8.h)]

9. Dans la section `protected`, définissez la méthode `propagate_to_any_targets`.

[!code-cpp[concrt-priority-buffer#9](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_9.h)]

   La méthode `propagate_to_any_targets` transfère le message qui se trouve au début de la file d’attente d’entrée vers la file d’attente de sortie et propage tous les messages de la file d’attente de sortie.

10. Dans la section `protected`, définissez la méthode `accept_message`.

[!code-cpp[concrt-priority-buffer#8](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_10.h)]

   Lorsqu’un bloc cible appelle la méthode `accept_message`, la classe `priority_buffer` transfère la propriété du message au premier bloc cible qui l’accepte. (Cela ressemble au comportement de `unbounded_buffer`.)

11. Dans la section `protected`, définissez la méthode `reserve_message`.

[!code-cpp[concrt-priority-buffer#10](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_11.h)]

   La classe `priority_buffer` permet à un bloc cible de réserver un message lorsque l’identificateur de message fourni correspond à l’identificateur du message qui se trouve au début de la file d’attente. En d’autres termes, une cible peut réserver le message si l’objet `priority_buffer` n’a pas encore reçu de message supplémentaire et n’a pas encore propagé le message actuel.

12. Dans la section `protected`, définissez la méthode `consume_message`.

[!code-cpp[concrt-priority-buffer#11](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_12.h)]

   Un bloc cible appelle `consume_message` pour transférer la propriété du message qu’il A réservé.

13. Dans la section `protected`, définissez la méthode `release_message`.

[!code-cpp[concrt-priority-buffer#12](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_13.h)]

   Un bloc cible appelle `release_message` pour annuler sa réservation à un message.

14. Dans la section `protected`, définissez la méthode `resume_propagation`.

[!code-cpp[concrt-priority-buffer#13](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_14.h)]

   Le runtime appelle `resume_propagation` une fois qu’un bloc cible consomme ou libère un message réservé. Cette méthode propage tous les messages qui se trouvent dans la file d’attente de sortie.

15. Dans la section `protected`, définissez la méthode `link_target_notification`.

[!code-cpp[concrt-priority-buffer#14](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_15.h)]

   La variable membre `_M_pReservedFor` est définie par la classe de base, `source_block`. Cette variable membre pointe vers le bloc cible, le cas échéant, qui détient une réservation vers le message qui se trouve au début de la file d’attente de sortie. Le runtime appelle `link_target_notification` lorsqu’une nouvelle cible est liée à l’objet `priority_buffer`. Cette méthode propage tous les messages qui se trouvent dans la file d’attente de sortie si aucune cible ne détient de réservation.

16. Dans la section `private`, définissez la méthode `propagate_priority_order`.

[!code-cpp[concrt-priority-buffer#15](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_16.h)]

   Cette méthode propage tous les messages de la file d’attente de sortie. Chaque message de la file d’attente est offert à chaque bloc cible jusqu’à ce que l’un des blocs cibles accepte le message. La classe `priority_buffer` conserve l’ordre des messages sortants. Par conséquent, le premier message de la file d’attente de sortie doit être accepté par un bloc cible avant que cette méthode n’offre un autre message aux blocs cibles.

17. Dans la section `protected`, définissez la méthode `propagate_message`.

[!code-cpp[concrt-priority-buffer#16](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_17.h)]

   La méthode `propagate_message` permet à la classe `priority_buffer` d’agir en tant que récepteur de message ou cible. Cette méthode reçoit le message qui est proposé par le bloc source fourni et insère ce message dans la file d’attente de priorité. La méthode `propagate_message` envoie ensuite de manière asynchrone tous les messages de sortie aux blocs cibles.

   Le runtime appelle cette méthode lorsque vous appelez la fonction [Concurrency :: asend](reference/concurrency-namespace-functions.md#asend) ou lorsque le bloc de message est connecté à d’autres blocs de message.

18. Dans la section `protected`, définissez la méthode `send_message`.

[!code-cpp[concrt-priority-buffer#17](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_18.h)]

   La méthode `send_message` ressemble à `propagate_message`. Toutefois, il envoie les messages de sortie de façon synchrone plutôt qu’en mode asynchrone.

   Le runtime appelle cette méthode pendant une opération d’envoi synchrone, par exemple quand vous appelez la fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) .

La classe `priority_buffer` contient des surcharges de constructeur qui sont typiques dans de nombreux types de blocs de message. Certaines surcharges de constructeur prennent des objets [Concurrency :: Scheduler](../../parallel/concrt/reference/scheduler-class.md) ou [Concurrency :: ScheduleGroup](../../parallel/concrt/reference/schedulegroup-class.md) , qui permettent de gérer le bloc de message par un planificateur de tâches spécifique. D’autres surcharges de constructeur prennent une fonction de filtre. Les fonctions de filtre permettent aux blocs de messages d’accepter ou de rejeter un message en fonction de sa charge utile. Pour plus d’informations sur les filtres de messages, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md). Pour plus d’informations sur les planificateurs de tâches, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Étant donné que la classe `priority_buffer` trie les messages par priorité, puis par l’ordre dans lequel les messages sont reçus, cette classe est particulièrement utile lorsqu’elle reçoit des messages de manière asynchrone, par exemple, quand vous appelez la fonction [Concurrency :: asend](reference/concurrency-namespace-functions.md#asend) ou lorsque le bloc de message est connecté à d’autres blocs de messages.

[[Haut](#top)]

## <a name="complete"></a>L’exemple complet

L’exemple suivant illustre la définition complète de la classe `priority_buffer`.

[!code-cpp[concrt-priority-buffer#18](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_19.h)]

L’exemple suivant exécute simultanément un certain nombre d’opérations de `asend` et d' [accès concurrentiel :: Receive](reference/concurrency-namespace-functions.md#receive) sur un objet `priority_buffer`.

[!code-cpp[concrt-priority-buffer#19](../../parallel/concrt/codesnippet/cpp/walkthrough-creating-a-custom-message-block_20.cpp)]

Cet exemple produit l’exemple de sortie suivant.

```Output
36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36 36
24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24 24
12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12 12
```

La classe `priority_buffer` trie les messages d’abord par priorité, puis par ordre de réception des messages. Dans cet exemple, les messages avec une priorité numérique supérieure sont insérés vers le début de la file d’attente.

[[Haut](#top)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez la définition de la classe `priority_buffer` dans un fichier nommé `priority_buffer.h` et le programme de test dans un fichier nommé `priority_buffer.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL. exe/EHsc priority_buffer. cpp**

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)
