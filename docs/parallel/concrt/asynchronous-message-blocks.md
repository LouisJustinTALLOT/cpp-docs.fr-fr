---
title: Blocs de messages asynchrones
ms.date: 11/04/2016
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
ms.openlocfilehash: 6697bdd296a3c71f03bc22986efa47dd586d5d9e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217907"
---
# <a name="asynchronous-message-blocks"></a>Blocs de messages asynchrones

La bibliothèque d’agents fournit plusieurs types de blocs de messages qui vous permettent de propager des messages entre les composants de l’application de manière thread-safe. Ces types de blocs de messages sont souvent utilisés avec les différentes routines de passage de message, telles que [Concurrency :: Send](reference/concurrency-namespace-functions.md#send), [Concurrency :: asend](reference/concurrency-namespace-functions.md#asend), [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive)et [Concurrency :: try_receive](reference/concurrency-namespace-functions.md#try_receive). Pour plus d’informations sur les routines de passage de message définies par la bibliothèque d’agents, consultez [fonctions de passage de message](../../parallel/concrt/message-passing-functions.md).

## <a name="sections"></a><a name="top"></a>Sections

Cette rubrique contient les sections suivantes :

- [Sources et cibles](#sources_and_targets)

- [Propagation des messages](#propagation)

- [Vue d’ensemble des types de bloc de message](#overview)

- [Classe unbounded_buffer](#unbounded_buffer)

- [Classe overwrite_buffer](#overwrite_buffer)

- [Classe single_assignment](#single_assignment)

- [Call (classe)](#call)

- [transformer, classe](#transformer)

- [Classe Choice](#choice)

- [Classes de jointure et de multitype_join](#join)

- [Timer (classe)](#timer)

- [Filtrage des messages](#filtering)

- [Réservation de messages](#reservation)

## <a name="sources-and-targets"></a><a name="sources_and_targets"></a>Sources et cibles

Les sources et les cibles sont deux participants importants au passage de messages. Une *source* fait référence à un point de terminaison de communication qui envoie des messages. Une *cible* fait référence à un point de terminaison de communication qui reçoit des messages. Vous pouvez considérer une source comme un point de terminaison à partir duquel vous lisez et une cible comme point de terminaison dans lequel vous écrivez. Les applications connectent les sources et les cibles ensemble pour former des *réseaux de messagerie*.

La bibliothèque d’agents utilise deux classes abstraites pour représenter les sources et les cibles : [Concurrency :: ISource](../../parallel/concrt/reference/isource-class.md) et [Concurrency :: ITarget](../../parallel/concrt/reference/itarget-class.md). Les types de blocs de messages qui agissent en tant que sources dérivent de `ISource` ; les types de blocs de messages qui agissent en tant que cibles dérivent de `ITarget` . Les types de blocs de messages qui jouent le rôle de sources et de cibles dérivent de `ISource` et `ITarget` .

[[Haut](#top)]

## <a name="message-propagation"></a><a name="propagation"></a>Propagation des messages

La *propagation de messages* est l’action consistant à envoyer un message d’un composant à un autre. Lorsqu’un message est proposé par un bloc de message, il peut accepter, refuser ou reporter ce message. Chaque type de bloc de message stocke et transmet les messages de différentes manières. Par exemple, la `unbounded_buffer` classe stocke un nombre illimité de messages, la `overwrite_buffer` classe stocke un seul message à la fois, et la classe transformer stocke une version modifiée de chaque message. Ces types de blocs de messages sont décrits plus en détail plus loin dans ce document.

Lorsqu’un bloc de message accepte un message, il peut éventuellement effectuer un travail et, si le bloc de message est une source, passer le message résultant à un autre membre du réseau. Un bloc de message peut utiliser une fonction de filtre pour refuser des messages qu’il ne souhaite pas recevoir. Les filtres sont décrits plus en détail plus loin dans cette rubrique, dans la section [filtrage des messages](#filtering). Un bloc de message qui diffère un message peut réserver ce message et le consommer ultérieurement. La réservation de messages est décrite plus en détail plus loin dans cette rubrique, dans la section [réservation de messages](#reservation).

La bibliothèque d’agents permet aux blocs de messages de transmettre des messages de manière asynchrone ou synchrone. Lorsque vous transmettez un message à un bloc de message de manière synchrone, par exemple à l’aide de la `send` fonction, le runtime bloque le contexte actuel jusqu’à ce que le bloc cible accepte ou rejette le message. Lorsque vous transmettez un message à un bloc de message de façon asynchrone, par exemple, à l’aide de la `asend` fonction, le runtime propose le message à la cible et, si la cible accepte le message, le runtime planifie une tâche asynchrone qui propage le message au récepteur. Le runtime utilise des tâches légères pour propager les messages de manière coopérative. Pour plus d’informations sur les tâches légères, consultez [Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).

Les applications connectent les sources et les cibles ensemble pour former des réseaux de messagerie. En règle générale, vous liez le réseau et appelez `send` ou `asend` pour transmettre des données au réseau. Pour connecter un bloc de message source à une cible, appelez la méthode [Concurrency :: ISource :: link_target](reference/isource-class.md#link_target) . Pour déconnecter un bloc source d’une cible, appelez la méthode [Concurrency :: ISource :: unlink_target](reference/isource-class.md#unlink_target) . Pour déconnecter un bloc source de toutes ses cibles, appelez la méthode [Concurrency :: ISource :: unlink_targets](reference/isource-class.md#unlink_targets) . Lorsque l’un des types de bloc de message prédéfinis quitte l’étendue ou est détruit, il se déconnecte automatiquement de tous les blocs cibles. Certains types de blocs de messages limitent le nombre maximal de cibles dans lesquelles ils peuvent écrire. La section suivante décrit les restrictions qui s’appliquent aux types de blocs de message prédéfinis.

[[Haut](#top)]

## <a name="overview-of-message-block-types"></a><a name="overview"></a>Vue d’ensemble des types de bloc de message

Le tableau suivant décrit brièvement le rôle des types de bloc de message importants.

[unbounded_buffer](#unbounded_buffer)<br/>
Stocke une file d’attente de messages.

[overwrite_buffer](#overwrite_buffer)<br/>
Stocke un message qui peut être écrit et lu à plusieurs moments.

[single_assignment](#single_assignment)<br/>
Stocke un message qui peut être écrit une fois et lu à plusieurs moments.

[call](#call)<br/>
Effectue un travail lorsqu’il reçoit un message.

[transformer](#transformer)<br/>
Effectue un travail lorsqu’il reçoit des données et envoie le résultat de ce travail à un autre bloc cible. La `transformer` classe peut agir sur différents types d’entrée et de sortie.

[choice](#choice)<br/>
Sélectionne le premier message disponible d’un ensemble de sources.

[jointure et jointure Multitype](#join)<br/>
Attendez que tous les messages soient reçus d’un ensemble de sources, puis combinez-les en un seul message pour un autre bloc de message.

[minute](#timer)<br/>
Envoie un message à un bloc cible à intervalles réguliers.

Ces types de blocs de messages ont des caractéristiques différentes qui les rendent utiles dans différentes situations. Voici quelques-unes des caractéristiques :

- *Type de propagation*: indique si le bloc de message agit comme une source de données, un récepteur de données, ou les deux.

- *Classement des messages*: indique si le bloc de message conserve l’ordre d’origine dans lequel les messages sont envoyés ou reçus. Chaque type de bloc de message prédéfini conserve l’ordre d’origine dans lequel il envoie ou reçoit des messages.

- *Nombre de sources : nombre*maximal de sources à partir desquelles le bloc de message peut lire.

- *Nombre de cibles : nombre*maximal de cibles dans lesquelles le bloc de message peut écrire.

Le tableau suivant montre comment ces caractéristiques sont liées aux différents types de bloc de message.

|Type de bloc de message|Type de propagation (source, cible, ou les deux)|Classement des messages (ordonné ou non ordonné)|Nombre de sources|Nombre de cibles|
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|
|`unbounded_buffer`|Les deux|Ordered (Validée)|Nonlié|Nonlié|
|`overwrite_buffer`|Les deux|Ordered (Validée)|Nonlié|Nonlié|
|`single_assignment`|Les deux|Ordered (Validée)|Nonlié|Nonlié|
|`call`|Cible|Ordered (Validée)|Nonlié|Non applicable|
|`transformer`|Les deux|Ordered (Validée)|Nonlié|1|
|`choice`|Les deux|Ordered (Validée)|10|1|
|`join`|Les deux|Ordered (Validée)|Nonlié|1|
|`multitype_join`|Les deux|Ordered (Validée)|10|1|
|`timer`|Source|Non applicable|Non applicable|1|

Les sections suivantes décrivent les types de blocs de messages plus en détail.

[[Haut](#top)]

## <a name="unbounded_buffer-class"></a><a name="unbounded_buffer"></a>Classe unbounded_buffer

La classe [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) représente une structure de messagerie asynchrone à usage général. Cette classe stocke une file d'attente de messages de type premier entré, premier sorti (FIFO). Plusieurs cibles peuvent lire ces messages et plusieurs sources peuvent y écrire. Quand une cible reçoit un message d’un `unbounded_buffer` objet, ce message est supprimé de la file d’attente de messages. Par conséquent, bien qu’un `unbounded_buffer` objet puisse avoir plusieurs cibles, une seule cible recevra chaque message. La classe `unbounded_buffer` est utile quand vous voulez transmettre plusieurs messages à un autre composant et que ce composant doit recevoir chaque message.

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `unbounded_buffer` classe. Cet exemple envoie trois valeurs à un `unbounded_buffer` objet, puis lit ces valeurs à partir du même objet.

[!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]

Cet exemple produit la sortie suivante :

```Output
334455
```

Pour obtenir un exemple complet qui montre comment utiliser la `unbounded_buffer` classe, consultez [Comment : implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Haut](#top)]

## <a name="overwrite_buffer-class"></a><a name="overwrite_buffer"></a>Classe overwrite_buffer

La classe [Concurrency :: overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) ressemble à la `unbounded_buffer` classe, à ceci près qu’un `overwrite_buffer` objet stocke un seul message. En outre, lorsqu’une cible reçoit un message d’un `overwrite_buffer` objet, ce message n’est pas supprimé de la mémoire tampon. Par conséquent, plusieurs cibles reçoivent une copie du message.

La `overwrite_buffer` classe est utile lorsque vous souhaitez transmettre plusieurs messages à un autre composant, mais que ce composant n’a besoin que de la valeur la plus récente. Cette classe est également utile quand vous voulez diffuser un message vers plusieurs composants.

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `overwrite_buffer` classe. Cet exemple envoie trois valeurs à un `overwrite _buffer` objet, puis lit trois fois la valeur actuelle à partir du même objet. Cet exemple est similaire à l’exemple de la `unbounded_buffer` classe. Toutefois, la `overwrite_buffer` classe stocke un seul message. En outre, le runtime ne supprime pas le message d’un `overwrite_buffer` objet après sa lecture.

[!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]

Cet exemple produit la sortie suivante :

```Output
555555
```

Pour obtenir un exemple complet qui montre comment utiliser la `overwrite_buffer` classe, consultez [Comment : implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).

[[Haut](#top)]

## <a name="single_assignment-class"></a><a name="single_assignment"></a>Classe single_assignment

La classe [Concurrency :: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) ressemble à la `overwrite_buffer` classe, à ceci près qu’un `single_assignment` objet ne peut être écrit qu’une seule fois. Comme pour la classe `overwrite_buffer`, quand une cible reçoit un message d'un objet `single_assignment`, le message n'est pas supprimé de l'objet. Par conséquent, plusieurs cibles reçoivent une copie du message. La `single_assignment` classe est utile lorsque vous souhaitez diffuser un message vers plusieurs composants.

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `single_assignment` classe. Cet exemple envoie trois valeurs à un `single_assignment` objet, puis lit trois fois la valeur actuelle à partir du même objet. Cet exemple est similaire à l’exemple de la `overwrite_buffer` classe. Bien que les `overwrite_buffer` `single_assignment` classes et stockent un seul message, la `single_assignment` classe ne peut être écrite qu’une seule fois.

[!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]

Cet exemple produit la sortie suivante :

```Output
333333
```

Pour obtenir un exemple complet qui montre comment utiliser la `single_assignment` classe, consultez [procédure pas à pas : implémentation de futures](../../parallel/concrt/walkthrough-implementing-futures.md).

[[Haut](#top)]

## <a name="call-class"></a><a name="call"></a>Call (classe)

La classe [Concurrency :: Call](../../parallel/concrt/reference/call-class.md) agit comme un récepteur de messages qui exécute une fonction de travail lorsqu’elle reçoit des données. Cette fonction de travail peut être une expression lambda, un objet de fonction ou un pointeur de fonction. Un `call` objet se comporte différemment d’un appel de fonction ordinaire, car il agit parallèlement à d’autres composants qui lui envoient des messages. Si un `call` objet effectue un travail lorsqu’il reçoit un message, il ajoute ce message à une file d’attente. Chaque `call` objet traite les messages mis en file d’attente dans l’ordre dans lequel ils sont reçus.

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `call` classe. Cet exemple crée un `call` objet qui imprime chaque valeur qu’il reçoit sur la console. L’exemple envoie ensuite trois valeurs à l' `call` objet. Étant donné que l' `call` objet traite des messages sur un thread séparé, cet exemple utilise également une variable de compteur et un objet d' [événement](../../parallel/concrt/reference/event-class.md) pour s’assurer que l' `call` objet traite tous les messages avant le retour de la `wmain` fonction.

[!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]

Cet exemple produit la sortie suivante :

```Output
334455
```

Pour obtenir un exemple complet qui montre comment utiliser la `call` classe, consultez [Comment : fournir des fonctions de travail aux classes Call et transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).

[[Haut](#top)]

## <a name="transformer-class"></a><a name="transformer"></a>transformer, classe

La classe [Concurrency :: transformer](../../parallel/concrt/reference/transformer-class.md) agit à la fois comme un destinataire de message et comme expéditeur de message. La `transformer` classe ressemble à la `call` classe, car elle exécute une fonction de travail définie par l’utilisateur lorsqu’elle reçoit des données. Toutefois, la `transformer` classe envoie également le résultat de la fonction de travail aux objets récepteur. À l’instar d’un `call` objet, un `transformer` objet agit en parallèle à d’autres composants qui lui envoient des messages. Si un `transformer` objet effectue un travail lorsqu’il reçoit un message, il ajoute ce message à une file d’attente. Chaque `transformer` objet traite ses messages mis en file d’attente dans l’ordre dans lequel ils sont reçus.

La `transformer` classe envoie son message à une cible. Si vous affectez au `_PTarget` paramètre dans le constructeur la valeur `NULL` , vous pouvez spécifier ultérieurement la cible en appelant la méthode [Concurrency :: link_target](reference/source-block-class.md#link_target) .

Contrairement à tous les autres types de blocs de messages asynchrones fournis par la bibliothèque d’agents, la `transformer` classe peut agir sur différents types d’entrée et de sortie. Cette capacité à transformer des données d’un type en un autre fait de la `transformer` classe un composant clé dans de nombreux réseaux simultanés. En outre, vous pouvez ajouter des fonctionnalités parallèles plus précises dans la fonction de travail d’un `transformer` objet.

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `transformer` classe. Cet exemple crée un `transformer` objet qui multiple chaque valeur d’entrée de 0,33 afin de **`int`** produire une **`double`** valeur comme sortie. L’exemple reçoit ensuite les valeurs transformées à partir du même `transformer` objet et les affiche dans la console.

[!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]

Cet exemple produit la sortie suivante :

```Output
10.8914.5218.15
```

Pour obtenir un exemple complet qui montre comment utiliser la `transformer` classe, consultez [How to : Use transformer in a data pipeline](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).

[[Haut](#top)]

## <a name="choice-class"></a><a name="choice"></a>Classe Choice

La classe [Concurrency :: Choice](../../parallel/concrt/reference/choice-class.md) sélectionne le premier message disponible à partir d’un ensemble de sources. La `choice` classe représente un mécanisme de flux de contrôle au lieu d’un mécanisme de flux de données (la rubrique [bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) décrit les différences entre le flux de données et le flux de contrôle).

La lecture à partir d’un objet Choice ressemble à l’appel de la fonction API Windows `WaitForMultipleObjects` lorsque le paramètre a la `bWaitAll` valeur `FALSE` . Toutefois, la `choice` classe lie les données à l’événement lui-même plutôt qu’à un objet de synchronisation externe.

En général, vous utilisez la `choice` classe avec la fonction [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) pour piloter le workflow de contrôle dans votre application. Utilisez la `choice` classe lorsque vous devez effectuer une sélection parmi les tampons de messages qui ont des types différents. Utilisez la `single_assignment` classe lorsque vous devez effectuer une sélection parmi les tampons de messages qui ont le même type.

L’ordre dans lequel vous liez des sources à un `choice` objet est important, car il peut déterminer quel message est sélectionné. Par exemple, considérez le cas où vous liez plusieurs mémoires tampons de messages qui contiennent déjà un message à un `choice` objet. L' `choice` objet sélectionne le message de la première source à laquelle il est lié. Une fois que vous avez lié toutes les sources, l' `choice` objet conserve l’ordre dans lequel chaque source reçoit un message.

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `choice` classe. Cet exemple utilise la fonction [Concurrency :: make_choice](reference/concurrency-namespace-functions.md#make_choice) pour créer un `choice` objet qui effectue une sélection parmi trois blocs de message. L’exemple calcule ensuite différents nombres de Fibonacci et stocke chaque résultat dans un bloc de message différent. L’exemple imprime ensuite sur la console un message basé sur l’opération qui s’est terminée en premier.

[!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]

Cet exemple produit l’exemple de sortie suivant :

```Output
fib35 received its value first. Result = 9227465
```

Étant donné qu’il n’est pas garanti que la tâche qui calcule le nombre de Fibonacci 35<sup>th</sup> se termine en premier, la sortie de cet exemple peut varier.

Cet exemple utilise l’algorithme [Concurrency ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) pour calculer les nombres de Fibonacci en parallèle. Pour plus d’informations sur `parallel_invoke` , consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

Pour obtenir un exemple complet qui montre comment utiliser la `choice` classe, consultez [Comment : effectuer une sélection parmi les tâches terminées](../../parallel/concrt/how-to-select-among-completed-tasks.md).

[[Haut](#top)]

## <a name="join-and-multitype_join-classes"></a><a name="join"></a>Classes de jointure et de multitype_join

Les classes [Concurrency :: Join](../../parallel/concrt/reference/join-class.md) et [Concurrency :: multitype_join](../../parallel/concrt/reference/multitype-join-class.md) vous permettent d’attendre que chaque membre d’un ensemble de sources reçoive un message. La `join` classe agit sur les objets sources qui ont un type de message commun. La `multitype_join` classe agit sur des objets sources qui peuvent avoir des types de messages différents.

La lecture à partir d’un `join` `multitype_join` objet ou ressemble à l’appel de la fonction API Windows `WaitForMultipleObjects` lorsque le paramètre a la `bWaitAll` valeur `TRUE` . Toutefois, tout comme un `choice` objet, `join` les `multitype_join` objets utilisent un mécanisme d’événement qui lie les données à l’événement lui-même plutôt qu’à un objet de synchronisation externe.

La lecture à partir d’un `join` objet produit un objet std ::[Vector](../../standard-library/vector-class.md) . La lecture à partir d’un `multitype_join` objet produit un objet std ::[Tuple](../../standard-library/tuple-class.md) . Les éléments apparaissent dans ces objets dans le même ordre que leurs mémoires tampons sources correspondantes qui sont liées à l' `join` `multitype_join` objet ou. Étant donné que l’ordre dans lequel vous liez des mémoires tampons sources à un `join` `multitype_join` objet ou est associé à l’ordre des éléments dans l' `vector` objet ou le résultant, nous vous recommandons de ne `tuple` pas dissocier une mémoire tampon source existante d’une jointure. Cela peut entraîner un comportement non spécifié.

### <a name="greedy-versus-non-greedy-joins"></a>Jointures gourmandes et non gourmandes

Les `join` `multitype_join` classes et prennent en charge le concept de jointures gourmandes et non gourmandes. Une *jointure gourmande* accepte un message de chacune de ses sources à mesure que les messages sont disponibles jusqu’à ce que tous les messages soient disponibles. Une *jointure non gourmande* reçoit des messages en deux phases. Tout d’abord, une jointure non gourmande attend jusqu’à ce qu’un message de chacune de ses sources soit proposé. Deuxièmement, une fois que tous les messages sources sont disponibles, une jointure non gourmande tente de réserver chacun de ces messages. S’il peut réserver chaque message, il consomme tous les messages et les propage à sa cible. Dans le cas contraire, elle libère, ou annule, les réservations de message et attend à nouveau que chaque source reçoive un message.

Les jointures gourmandes sont plus performantes que les jointures non gourmandes, car elles acceptent immédiatement les messages. Toutefois, dans de rares cas, les jointures gourmandes peuvent entraîner des blocages. Utilisez une jointure non gourmande lorsque vous avez plusieurs jointures qui contiennent un ou plusieurs objets source partagés.

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `join` classe. Cet exemple utilise la fonction [Concurrency :: make_join](reference/concurrency-namespace-functions.md#make_join) pour créer un `join` objet qui reçoit de trois `single_assignment` objets. Cet exemple calcule différents nombres de Fibonacci, stocke chaque résultat dans un `single_assignment` objet différent, puis imprime sur la console chaque résultat que `join` contient l’objet. Cet exemple est similaire à l’exemple de la `choice` classe, à ceci près que la `join` classe attend que tous les blocs de messages sources reçoivent un message.

[!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]

Cet exemple produit la sortie suivante :

```Output
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008
```

Cet exemple utilise l’algorithme [Concurrency ::p arallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) pour calculer les nombres de Fibonacci en parallèle. Pour plus d’informations sur `parallel_invoke` , consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

Pour obtenir des exemples complets qui montrent comment utiliser la `join` classe, consultez Guide pratique pour effectuer une [sélection parmi les tâches terminées](../../parallel/concrt/how-to-select-among-completed-tasks.md) et [procédure pas à pas : utilisation de Join pour empêcher l’interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).

[[Haut](#top)]

## <a name="timer-class"></a><a name="timer"></a>Timer (classe)

La classe Concurrency ::[Timer](../../parallel/concrt/reference/timer-class.md) agit comme une source de message. Un `timer` objet envoie un message à une cible après l’expiration d’un laps de temps spécifié. La `timer` classe est utile lorsque vous devez différer l’envoi d’un message ou que vous souhaitez envoyer un message à intervalles réguliers.

La `timer` classe envoie son message à une seule cible. Si vous affectez au `_PTarget` paramètre dans le constructeur la valeur `NULL` , vous pouvez spécifier ultérieurement la cible en appelant la méthode [Concurrency :: ISource :: link_target](reference/source-block-class.md#link_target) .

Un `timer` objet peut se répéter ou ne pas se répéter. Pour créer un minuteur répétitif, transmettez **`true`** le `_Repeating` paramètre lorsque vous appelez le constructeur. Sinon, transmettez **`false`** le `_Repeating` paramètre pour créer un minuteur qui ne se répète pas. Si le minuteur se répète, il envoie le même message à sa cible après chaque intervalle.

La bibliothèque d’agents crée `timer` des objets dans l’état non démarré. Pour démarrer un objet Timer, appelez la méthode [Concurrency :: timer :: Start](reference/timer-class.md#start) . Pour arrêter un `timer` objet, détruisez l’objet ou appelez la méthode [Concurrency :: timer :: Stop](reference/timer-class.md#stop) . Pour suspendre un minuteur répétitif, appelez la méthode [Concurrency :: timer ::p ause](reference/timer-class.md#pause) .

### <a name="example"></a>Exemple

L’exemple suivant illustre la structure de base de l’utilisation de la `timer` classe. L’exemple utilise `timer` les `call` objets et pour signaler la progression d’une opération de longue durée.

[!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]

Cet exemple produit l’exemple de sortie suivant :

```Output
Computing fib(42)..................................................result is 267914296
```

Pour obtenir un exemple complet qui montre comment utiliser la `timer` classe, consultez [Comment : envoyer un message à intervalles réguliers](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).

[[Haut](#top)]

## <a name="message-filtering"></a><a name="filtering"></a>Filtrage des messages

Lorsque vous créez un objet de bloc de message, vous pouvez fournir une *fonction de filtre* qui détermine si le bloc de message accepte ou rejette un message. Une fonction de filtre est un moyen utile de garantir qu’un bloc de message ne reçoit que certaines valeurs.

L’exemple suivant montre comment créer un `unbounded_buffer` objet qui utilise une fonction de filtre pour accepter uniquement des nombres pairs. L' `unbounded_buffer` objet rejette les nombres impairs et, par conséquent, ne propage pas les nombres impairs à ses blocs cibles.

[!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]

Cet exemple produit la sortie suivante :

```Output
0 2 4 6 8
```

Une fonction de filtre peut être une fonction lambda, un pointeur de fonction ou un objet de fonction. Chaque fonction de filtre prend l’une des formes suivantes.

```Output
bool (T)
bool (T const &)
```

Pour éliminer la copie inutile des données, utilisez la deuxième forme lorsque vous avez un type d’agrégat qui est propagé par valeur.

Le filtrage des messages prend en charge le modèle de programmation de *flux* de données, dans lequel les composants effectuent des calculs lorsqu’ils reçoivent des données. Pour obtenir des exemples qui utilisent des fonctions de filtre pour contrôler le flux de données dans un message passant un réseau, consultez [Comment : utiliser un filtre de bloc de message](../../parallel/concrt/how-to-use-a-message-block-filter.md), [procédure pas à pas : création d’un agent de flux](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md)de données et [procédure pas à pas : création d’un réseau de traitement d’image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).

[[Haut](#top)]

## <a name="message-reservation"></a><a name="reservation"></a>Réservation de messages

La *réservation de messages* permet à un bloc de message de réserver un message pour une utilisation ultérieure. En règle générale, la réservation de messages n’est pas utilisée directement. Toutefois, la compréhension de la réservation des messages peut vous aider à mieux comprendre le comportement de certains types de blocs de message prédéfinis.

Envisagez les jointures non gourmandes et gourmandes. Les deux utilisent la réservation de messages pour réserver des messages en vue d’une utilisation ultérieure. Décrit précédemment, une jointure non gourmande reçoit des messages en deux phases. Pendant la première phase, un objet qui n’est pas gourmand `join` attend que chacune de ses sources reçoive un message. Une jointure non gourmande tente alors de réserver chacun de ces messages. S’il peut réserver chaque message, il consomme tous les messages et les propage à sa cible. Dans le cas contraire, elle libère, ou annule, les réservations de message et attend à nouveau que chaque source reçoive un message.

Une jointure gourmande, qui lit également les messages d’entrée d’un certain nombre de sources, utilise la réservation de messages pour lire des messages supplémentaires pendant qu’elle attend de recevoir un message de chaque source. Par exemple, considérez une jointure gourmande qui reçoit des messages des blocs de messages `A` et `B` . Si la jointure gourmande reçoit deux messages de B mais n’a pas encore reçu de message de `A` , la jointure gourmande enregistre l’identificateur de message unique pour le deuxième message à partir de `B` . Une fois que la jointure gourmande reçoit un message de `A` et propage ces messages, elle utilise l’identificateur de message enregistré pour voir si le deuxième message de `B` est toujours disponible.

Vous pouvez utiliser la réservation de messages lorsque vous implémentez vos propres types de blocs de messages personnalisés. Pour obtenir un exemple de création d’un type de bloc de message personnalisé, consultez [procédure pas à pas : création d’un bloc de message personnalisé](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)
