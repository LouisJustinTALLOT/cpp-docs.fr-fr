---
title: Blocs de messages asynchrones | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- non-greedy join [Concurrency Runtime]
- asynchronous message blocks
- greedy join [Concurrency Runtime]
ms.assetid: 79c456c0-1692-480c-bb67-98f2434c1252
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5de4a9ed20e20c03f44f8b8d421a628f220099f7
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695029"
---
# <a name="asynchronous-message-blocks"></a>Blocs de messages asynchrones

La bibliothèque d’Agents fournit plusieurs types de blocs de messages qui vous permettent de propager des messages entre composants d’application de manière thread-safe. Ces types de blocs de messages sont souvent utilisés avec les différentes routines de passage de messages, tels que [concurrency::send](reference/concurrency-namespace-functions.md#send), [concurrency::asend](reference/concurrency-namespace-functions.md#asend), [concurrency::receive](reference/concurrency-namespace-functions.md#receive), et [concurrency::try_receive](reference/concurrency-namespace-functions.md#try_receive). Pour plus d’informations sur les routines qui sont définies par la bibliothèque d’Agents de passage de messages, consultez [fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md).  
  
##  <a name="top"></a> Sections  
 Cette rubrique contient les sections suivantes :  
  
- [Sources et cibles](#sources_and_targets)  
  
- [Propagation de messages](#propagation)  
  
- [Vue d’ensemble des Types de blocs de Message](#overview)  
  
- [Classe unbounded_buffer](#unbounded_buffer)  
  
- [overwrite_buffer, classe](#overwrite_buffer)  
  
- [single_assignment, classe](#single_assignment)  
  
- [call, classe](#call)  
  
- [transformer, classe](#transformer)  
  
- [choice, classe](#choice)  
  
- [Classes de jointure et multitype_join](#join)  
  
- [timer, classe](#timer)  
  
- [Le filtrage des messages](#filtering)  
  
- [Réservation de messages](#reservation)  
  
##  <a name="sources_and_targets"></a> Sources et cibles  
 Sources et cibles sont deux participants importants au passage de message. A *source* fait référence à un point de terminaison de communication qui envoie des messages. A *cible* fait référence à un point de terminaison de communication qui reçoit des messages. Vous pouvez considérer une source comme un point de terminaison que vous lisez à partir d’et une cible en tant qu’un point de terminaison que vous écrivez pour. Connectent des applications sources et cibles ensemble pour former *réseaux de messagerie*.  
  
 La bibliothèque d’Agents utilise deux classes abstraites pour représenter les sources et cibles : [concurrency::ISource](../../parallel/concrt/reference/isource-class.md) et [concurrency::ITarget](../../parallel/concrt/reference/itarget-class.md). Les types de blocs de message qui agissent comme sources dérivent `ISource`; les types de blocs de message qui agissent comme cibles dérivent `ITarget`. Types de bloc de message qui agissent en tant que sources et cibles dérivent `ISource` et `ITarget`.  
  
 [[Haut](#top)]  
  
##  <a name="propagation"></a> Propagation de messages  
 *La propagation des messages* consiste à envoyer un message à partir d’un composant vers un autre. Lorsqu’un bloc de message reçoit un message, il peut accepter, refuser ou reporter. Chaque type de bloc de message stocke et transmet des messages de différentes façons. Par exemple, le `unbounded_buffer` classe stocke un nombre illimité de messages, la `overwrite_buffer` classe stocke un seul message à la fois, et la classe transformer stocke une version modifiée de chaque message. Ces types de blocs de messages sont décrits plus en détail plus loin dans ce document.  
  
 Lorsqu’un bloc de message accepte un message, il peut éventuellement effectuer le travail et, si le bloc de message est une source, passer le message résultant à un autre membre du réseau. Un bloc de message peut utiliser une fonction de filtre pour refuser les messages qu’il ne souhaite pas recevoir. Les filtres sont décrits plus en détail plus loin dans cette rubrique, dans la section [le filtrage des messages](#filtering). Un bloc de message qui diffère un message peut réserver ce message et l’utiliser ultérieurement. La réservation de messages est décrite plus en détail plus loin dans cette rubrique, dans la section [la réservation de messages](#reservation).  
  
 La bibliothèque d’Agents permet aux blocs de messages de façon asynchrone ou synchrone transmettre des messages. Lorsque vous passez un message à un bloc de message de façon synchrone, par exemple, à l’aide de la `send` (fonction), le runtime bloque le contexte actuel jusqu'à ce que le bloc cible accepte ou rejette le message. Lorsque vous passez un message à un bloc de message de façon asynchrone, par exemple, à l’aide de la `asend` (fonction), le runtime offre le message à la cible, et si la cible accepte le message, le runtime planifie une tâche asynchrone qui propage le message pour le récepteur. Le runtime utilise des tâches légères pour propager des messages de manière coopérative. Pour plus d’informations sur les tâches légères, consultez [du Planificateur de tâches](../../parallel/concrt/task-scheduler-concurrency-runtime.md).  
  

 Applications interconnecter sources et cibles pour former des réseaux de messagerie. En règle générale, vous liez le réseau et appelez `send` ou `asend` pour passer des données au réseau. Pour vous connecter à un bloc de message source vers une cible, appelez le [Concurrency::ISource :: link_target](reference/isource-class.md#link_target) méthode. Pour déconnecter un bloc source à partir d’une cible, appelez le [Concurrency::ISource :: unlink_target](reference/isource-class.md#unlink_target) (méthode). Pour déconnecter un bloc source à partir de toutes ses cibles, appelez le [Concurrency::ISource :: unlink_targets](reference/isource-class.md#unlink_targets) (méthode). Lorsqu’un des types de bloc de message prédéfinis quitte la portée ou est détruit, il se déconnecte automatiquement à partir de tous les blocs cibles. Certains types de bloc de message limitent le nombre maximal de cibles auxquelles ils peuvent écrire à. La section suivante décrit les restrictions qui s’appliquent aux types de blocs de messages prédéfinis.  
  
 [[Haut](#top)]  
  
##  <a name="overview"></a> Vue d’ensemble des Types de blocs de Message  
 Le tableau suivant décrit brièvement le rôle des types de blocs de messages important.  
  
 [unbounded_buffer](#unbounded_buffer)  
 Stocke une file d’attente de messages.  
  
 [overwrite_buffer](#overwrite_buffer)  
 Stocke un message qui peut être écrit à et lire à partir de plusieurs fois.  
  
 [single_assignment](#single_assignment)  
 Stocke un message qui peut être écrit dans une seule fois et lire à partir de plusieurs fois.  
  
 [call](#call)  
 Effectue un travail lorsqu’il reçoit un message.  
  
 [classe transformer](#transformer)  
 Effectue un travail lorsqu’il reçoit des données et envoie le résultat de ce travail à un autre bloc cible. La `transformer` classe peut agir sur différents types d’entrées et sortie.  
  
 [Choix](#choice)  
 Sélectionne le premier message disponible à partir d’un ensemble de sources.  
  
 [jointure et jointure multitype](#join)  
 Attendez que tous les messages reçus à partir d’un ensemble de sources et les combiner ensuite les messages dans un message pour un autre bloc de message.  
  
 [timer](#timer)  
 Envoie un message à un bloc cible à intervalles réguliers.  
  
 Ces types de blocs de messages ont des caractéristiques différentes qui les rendent utiles pour différentes situations. Voici quelques-unes des caractéristiques :  
  
- *Type de propagation*: indique si le bloc de message agit comme une source de données, un récepteur de données ou les deux.  
  
- *Classement des messages*: indique si le bloc de message conserve l’ordre d’origine dans lequel les messages sont envoyés ou reçus. Chaque type de bloc de message prédéfini conserve l’ordre d’origine dans lequel il envoie ou reçoit des messages.  
  
- *Nombre de source*: le nombre maximal de sources que le bloc de message peut lire.  
  
- *Nombre de cibles*: le nombre maximal de cibles qui le bloc de message peut écrire.  
  
 Le tableau suivant montre comment ces caractéristiques sont liés aux différents types de blocs de messages.  
  
|Type de bloc de message|Type de propagation (Source, cible ou les deux)|Message de commande (ordonné ou non ordonné)|Nombre de sources|Nombre de cibles|  
|------------------------|--------------------------------------------------|-----------------------------------------------|------------------|------------------|  
|`unbounded_buffer`|Both|Ordered|non liée|non liée|  
|`overwrite_buffer`|Both|Ordered|non liée|non liée|  
|`single_assignment`|Both|Ordered|non liée|non liée|  
|`call`|une cible|Ordered|non liée|Non applicable|  
|`transformer`|Both|Ordered|non liée|1|  
|`choice`|Both|Ordered|10|1|  
|`join`|Both|Ordered|non liée|1|  
|`multitype_join`|Both|Ordered|10|1|  
|`timer`|Source|Non applicable|Non applicable|1|  
  
 Les sections suivantes décrivent les types de bloc de message plus en détail.  
  
 [[Haut](#top)]  
  
##  <a name="unbounded_buffer"></a> Classe unbounded_buffer  
 Le [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) classe représente une structure de messagerie asynchrone à usage général. Cette classe stocke une file d'attente de messages de type premier entré, premier sorti (FIFO). Plusieurs cibles peuvent lire ces messages et plusieurs sources peuvent y écrire. Quand une cible reçoit un message à partir d’un `unbounded_buffer` de l’objet, ce message est supprimé de la file d’attente. Par conséquent, bien qu’un `unbounded_buffer` objet peut avoir plusieurs cibles, seule une cible reçoit chaque message. La classe `unbounded_buffer` est utile quand vous voulez transmettre plusieurs messages à un autre composant et que ce composant doit recevoir chaque message.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre la structure de base de l’utilisation avec la `unbounded_buffer` classe. Cet exemple envoie trois valeurs à un `unbounded_buffer` de l’objet, puis lit ces valeurs à partir du même objet.  
  
 [!code-cpp[concrt-unbounded_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_1.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
334455  
```  
  
 Pour obtenir un exemple complet qui montre comment utiliser le `unbounded_buffer` de classe, consultez [Comment : implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).  
  
 [[Haut](#top)]  
  
##  <a name="overwrite_buffer"></a> Classe overwrite_buffer  
 Le [concurrency::overwrite_buffer](../../parallel/concrt/reference/overwrite-buffer-class.md) ressemble à la `unbounded_buffer` classe, à ceci près qu’un `overwrite_buffer` objet stocke seulement un message. En outre, quand une cible reçoit un message à partir d’un `overwrite_buffer` de l’objet, ce message n’est pas supprimé de la mémoire tampon. Par conséquent, plusieurs cibles reçoivent une copie du message.  
  
 La `overwrite_buffer` classe est utile lorsque vous souhaitez transmettre plusieurs messages à un autre composant, mais que ce composant nécessite uniquement la valeur la plus récente. Cette classe est également utile quand vous voulez diffuser un message vers plusieurs composants.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre la structure de base de l’utilisation avec la `overwrite_buffer` classe. Cet exemple envoie trois valeurs à un `overwrite _buffer` de l’objet, puis lit la valeur actuelle à partir du même objet trois fois. Cet exemple est semblable à l’exemple pour la `unbounded_buffer` classe. Toutefois, la `overwrite_buffer` classe stocke seulement un message. En outre, le runtime ne supprime pas le message à partir d’un `overwrite_buffer` après qu’il a lu l’objet.  
  
 [!code-cpp[concrt-overwrite_buffer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_2.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
555555  
```  
  
 Pour obtenir un exemple complet qui montre comment utiliser le `overwrite_buffer` de classe, consultez [Comment : implémenter divers modèles de producteur-consommateur](../../parallel/concrt/how-to-implement-various-producer-consumer-patterns.md).  
  
 [[Haut](#top)]  
  
##  <a name="single_assignment"></a> Classe single_assignment  
 Le [concurrency::single_assignment](../../parallel/concrt/reference/single-assignment-class.md) ressemble à la `overwrite_buffer` classe, à ceci près qu’un `single_assignment` objet peut être écrites dans une seule fois. Comme pour la classe `overwrite_buffer`, quand une cible reçoit un message d'un objet `single_assignment`, le message n'est pas supprimé de l'objet. Par conséquent, plusieurs cibles reçoivent une copie du message. La `single_assignment` classe est utile lorsque vous souhaitez diffuser un message à plusieurs composants.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre la structure de base de l’utilisation avec la `single_assignment` classe. Cet exemple envoie trois valeurs à un `single_assignment` de l’objet, puis lit la valeur actuelle à partir du même objet trois fois. Cet exemple est semblable à l’exemple pour la `overwrite_buffer` classe. Bien qu’à la fois le `overwrite_buffer` et `single_assignment` classes stocker un seul message, la `single_assignment` classe peut être écrites dans une seule fois.  
  
 [!code-cpp[concrt-single_assignment-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_3.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
333333  
```  
  
 Pour obtenir un exemple complet qui montre comment utiliser le `single_assignment` de classe, consultez [procédure pas à pas : implémentation de tâches Futures](../../parallel/concrt/walkthrough-implementing-futures.md).  
  
 [[Haut](#top)]  
  
##  <a name="call"></a> Call, classe  
 Le [concurrency::call](../../parallel/concrt/reference/call-class.md) sert de classe de récepteur de message qui exécute une fonction de travail lorsqu’il reçoit des données. Cette fonction de travail peut être une expression lambda, un objet de fonction ou un pointeur de fonction. A `call` objet se comporte différemment d’un appel de fonction ordinaire, car il agit en parallèle à d’autres composants qui envoient des messages. Si un `call` objet exécute un travail lorsqu’il reçoit un message, il ajoute ce message à une file d’attente. Chaque `call` processus de l’objet en file d’attente de messages dans l’ordre dans lequel ils sont reçus.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre la structure de base de l’utilisation avec la `call` classe. Cet exemple crée un `call` objet qui imprime chaque valeur qu’il reçoit à la console. L’exemple envoie ensuite les trois valeurs pour la `call` objet. Car le `call` objet traite les messages sur un thread séparé, cet exemple utilise également une variable de compteur et une [événement](../../parallel/concrt/reference/event-class.md) objet pour vous assurer que le `call` objet traite tous les messages avant du `wmain` Retourne une fonction.  
  
 [!code-cpp[concrt-call-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_4.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
334455  
```  
  
 Pour obtenir un exemple complet qui montre comment utiliser le `call` de classe, consultez [Comment : fournir des fonctions de travail aux Classes call et transformer](../../parallel/concrt/how-to-provide-work-functions-to-the-call-and-transformer-classes.md).  
  
 [[Haut](#top)]  
  
##  <a name="transformer"></a> Classe transformer  
 Le [concurrency::transformer](../../parallel/concrt/reference/transformer-class.md) classe agit comme un récepteur du message et un expéditeur de message. Le `transformer` ressemble à la `call` classe, car elle effectue une fonction de travail définis par l’utilisateur lorsqu’il reçoit des données. Toutefois, la `transformer` classe envoie également le résultat de la fonction de travail pour les objets de récepteur. Comme un `call` objet, un `transformer` objet agit en parallèle à d’autres composants qui envoient des messages. Si un `transformer` objet exécute un travail lorsqu’il reçoit un message, il ajoute ce message à une file d’attente. Chaque `transformer` objet traite ses messages en file d’attente dans l’ordre dans lequel ils sont reçus.  
  
 La `transformer` classe envoie son message à une cible. Si vous définissez la `_PTarget` dans le constructeur pour `NULL`, vous pouvez spécifier ultérieurement la cible en appelant le [concurrency::link_target](reference/source-block-class.md#link_target) (méthode).  
  
 Contrairement à tous les autres types de blocs de messages asynchrones fournis par la bibliothèque d’Agents, le `transformer` classe peut agir sur différents types d’entrées et sortie. Cette capacité à transformer des données à partir d’un type en un autre fait la `transformer` classe d’un rôle essentiel dans de nombreux réseaux simultanés. En outre, vous pouvez ajouter plus de fonctionnalités parallèles affinées dans la fonction de travail d’un `transformer` objet.  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre la structure de base de l’utilisation avec la `transformer` classe. Cet exemple crée un `transformer` et multiplie chaque d’entrée de l’objet `int` valeur 0,33 afin de produire un `double` valeur en tant que sortie. L’exemple reçoit ensuite les valeurs transformées à partir de la même `transformer` de l’objet et les affiche sur la console.  
  
 [!code-cpp[concrt-transformer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_5.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
10.8914.5218.15  
```  
  
 Pour obtenir un exemple complet qui montre comment utiliser le `transformer` de classe, consultez [Comment : utiliser la classe transformer dans un Pipeline de données](../../parallel/concrt/how-to-use-transformer-in-a-data-pipeline.md).  
  
 [[Haut](#top)]  
  
##  <a name="choice"></a> Classe Choice  
 Le [classes concurrency::choice](../../parallel/concrt/reference/choice-class.md) classe sélectionne le premier message disponible dans un jeu de sources. Le `choice` classe représente un mécanisme de flux de contrôle au lieu d’un mécanisme de flux de données (la rubrique [bibliothèque d’Agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md) décrit les différences entre les flux de données et de flux de contrôle).  
  
 La lecture à partir d’un objet choice s’apparente à l’appel de la fonction API Windows `WaitForMultipleObjects` lorsqu’il a la `bWaitAll` paramètre la valeur `FALSE`. Toutefois, la `choice` classe lie des données à l’événement lui-même plutôt qu’à un objet de synchronisation externe.  
  

 En général, vous utilisez la `choice` classe avec le [concurrency::receive](reference/concurrency-namespace-functions.md#receive) fonction pour piloter le flux de contrôle dans votre application. Utilisez la `choice` classe lorsque vous devez sélectionner parmi des tampons de messages qui ont des types différents. Utilisez le `single_assignment` lorsque vous devez sélectionner parmi des tampons de messages qui ont le même type de classe.  

  
 L’ordre dans lequel vous liez les sources à un `choice` objet est important car il peut déterminer quel message est sélectionné. Par exemple, considérez le cas où vous liez plusieurs tampons de messages qui contiennent déjà un message à un `choice` objet. Le `choice` objet sélectionne le message à partir de la première source auquel il est lié. Après avoir lié toutes les sources, les `choice` objet conserve l’ordre dans lequel chaque source reçoit un message.  
  
### <a name="example"></a>Exemple  

 L’exemple suivant montre la structure de base de l’utilisation avec la `choice` classe. Cet exemple utilise le [concurrency::make_choice](reference/concurrency-namespace-functions.md#make_choice) fonction permettant de créer un `choice` objet sélectionne parmi les trois blocs de messages. L’exemple calcule plusieurs nombres de Fibonacci et stocke chaque résultat dans un bloc de message différent. L’exemple imprime ensuite à la console un message basé sur l’opération qui se termine en premier.  

  
 [!code-cpp[concrt-choice-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_6.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
fib35 received its value first. Result = 9227465  
```  
  
 Étant donné que la tâche qui calcule le 35<sup>th</sup> n’est pas garanti que le nombre de Fibonacci termine d’abord, la sortie de cet exemple peut varier.  
  

 Cet exemple utilise le [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme pour calculer les nombres de Fibonacci en parallèle. Pour plus d’informations sur `parallel_invoke`, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).  
  
 Pour obtenir un exemple complet qui montre comment utiliser le `choice` de classe, consultez [Comment : sélectionner parmi les tâches achevées](../../parallel/concrt/how-to-select-among-completed-tasks.md).  
  
 [[Haut](#top)]  
  
##  <a name="join"></a> Classes de jointure et multitype_join  
 Le [concurrency::join](../../parallel/concrt/reference/join-class.md) et [concurrency::multitype_join](../../parallel/concrt/reference/multitype-join-class.md) classes vous permettent d’attendre que chaque membre d’un ensemble de sources de recevoir un message. La `join` classe agit sur les objets sources qui ont un type de message commun. La `multitype_join` classe agit sur les objets sources qui peuvent avoir différents types de message.  
  
 Lecture à partir d’un `join` ou `multitype_join` objet ressemble à l’appel de la fonction API Windows `WaitForMultipleObjects` lorsqu’il a la `bWaitAll` paramètre la valeur `TRUE`. Toutefois, tout comme un `choice` objet, `join` et `multitype_join` objets utilisent un mécanisme d’événement qui lie les données à l’événement lui-même plutôt qu’à un objet de synchronisation externe.  
  
 Lecture à partir d’un `join` objet génère std ::[vecteur](../../standard-library/vector-class.md) objet. Lecture à partir d’un `multitype_join` objet génère std ::[tuple](../../standard-library/tuple-class.md) objet. Les éléments apparaissent dans ces objets dans le même ordre que leurs mémoires tampons sources correspondantes sont liées à la `join` ou `multitype_join` objet. Étant donné que l’ordre dans lequel vous liez source met en mémoire tampon pour un `join` ou `multitype_join` objet est associé à l’ordre des éléments dans la boîte `vector` ou `tuple` de l’objet, nous vous recommandons de ne pas dissocier un mémoire tampon source à partir d’un jointure. Cela peut entraîner un comportement non spécifié.  
  
### <a name="greedy-versus-non-greedy-joins"></a>Comportements gourmand et jointures Non gourmandes  
 Le `join` et `multitype_join` classes prennent en charge le concept de jointures non gourmandes et. A *jointure gourmande* accepte un message de chacune de ses sources que les messages deviennent disponibles jusqu'à ce que tous les messages sont disponibles. A *jointure non gourmande* reçoit les messages en deux phases. Tout d’abord, une jointure non gourmande attend jusqu'à ce qu’il reçoit un message à partir de chacune de ses sources. Ensuite, une fois que tous les messages sources sont disponibles, une jointure non gourmande tente de réserver chacun de ces messages. Si chaque message peut être réservé, elle consomme tous les messages et les propage à sa cible. Dans le cas contraire, il libère, ou annule, les réservations de message et attend une nouvelle fois pour chaque source de recevoir un message.  
  
 Jointures gourmandes plus performantes que les jointures non gourmandes, car ils acceptent les messages immédiatement. Toutefois, dans de rares cas, jointures gourmandes peuvent provoquer des interblocages. Utilisez une jointure non gourmande lorsque vous avez plusieurs jointures qui contiennent un ou plusieurs objets sources partagés.  
  
### <a name="example"></a>Exemple  

 L’exemple suivant montre la structure de base de l’utilisation avec la `join` classe. Cet exemple utilise le [concurrency::make_join](reference/concurrency-namespace-functions.md#make_join) fonction permettant de créer un `join` objet qui reçoit de trois `single_assignment` objets. Cet exemple calcule plusieurs nombres de Fibonacci, stocke chaque résultat dans une autre `single_assignment` objet et puis imprime sur la console du résultat qui le `join` contient l’objet. Cet exemple est semblable à l’exemple pour la `choice` classe, à ceci près que la `join` classe attend que tous les blocs de message source recevoir un message.  
  
 [!code-cpp[concrt-join-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_7.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
fib35 = 9227465fib37 = 24157817half_of_fib42 = 1.33957e+008  
```  

 Cet exemple utilise le [concurrency::parallel_invoke](reference/concurrency-namespace-functions.md#parallel_invoke) algorithme pour calculer les nombres de Fibonacci en parallèle. Pour plus d’informations sur `parallel_invoke`, consultez [des algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).  
  
 Pour obtenir des exemples complets qui montrent comment utiliser le `join` de classe, consultez [Comment : sélectionner parmi les tâches achevées](../../parallel/concrt/how-to-select-among-completed-tasks.md) et [procédure pas à pas : à l’aide de la classe join pour empêcher l’interblocage](../../parallel/concrt/walkthrough-using-join-to-prevent-deadlock.md).  
  
 [[Haut](#top)]  
  
##  <a name="timer"></a> Classe Timer  
 La concurrence ::[classe timer](../../parallel/concrt/reference/timer-class.md) agit comme une source de message. A `timer` objet envoie un message à une cible après une période de temps écoulé. La `timer` classe est utile lorsque vous devez différer l’envoi d’un message ou que vous souhaitez envoyer un message à intervalles réguliers.  
  

 La `timer` classe envoie son message à une cible qu’une seule. Si vous définissez la `_PTarget` dans le constructeur pour `NULL`, vous pouvez spécifier ultérieurement la cible en appelant le [Concurrency::ISource :: link_target](reference/source-block-class.md#link_target) méthode.  

  
 A `timer` objet peut être répété ou non extensible. Pour créer une minuterie répétitive, passez `true` pour la `_Repeating` paramètre lorsque vous appelez le constructeur. Sinon, passez `false` pour la `_Repeating` paramètre pour créer une minuterie non extensible. Si la minuterie est extensible, il envoie le même message à sa cible après chaque intervalle.  
  
 La bibliothèque d’Agents crée `timer` objets dans l’état non démarré. Pour démarrer un objet timer, appelez le [Concurrency::Timer :: Start](reference/timer-class.md#start) (méthode). Pour arrêter un `timer` d’objet, détruire l’objet ou l’appel de la [concurrency::timer::stop](reference/timer-class.md#stop) (méthode). Pour suspendre une minuterie répétitive, appelez le [concurrency::timer::pause](reference/timer-class.md#pause) (méthode).  
  
### <a name="example"></a>Exemple  
 L’exemple suivant montre la structure de base de l’utilisation avec la `timer` classe. L’exemple utilise `timer` et `call` objets pour signaler la progression d’une opération longue.  
  
 [!code-cpp[concrt-timer-structure#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_8.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
Computing fib(42)..................................................result is 267914296  
```  
  
 Pour obtenir un exemple complet qui montre comment utiliser le `timer` de classe, consultez [Comment : envoyer un Message à intervalles réguliers](../../parallel/concrt/how-to-send-a-message-at-a-regular-interval.md).  
  
 [[Haut](#top)]  
  
##  <a name="filtering"></a> Le filtrage des messages  
 Lorsque vous créez un objet de bloc de message, vous pouvez fournir un *fonction filter* qui détermine si le bloc de message accepte ou rejette un message. Une fonction de filtre est un moyen utile pour garantir qu’un bloc de message reçoit uniquement certaines valeurs.  
  
 L’exemple suivant montre comment créer un `unbounded_buffer` objet qui utilise une fonction de filtre pour accepter uniquement les nombres pairs. Le `unbounded_buffer` objet rejette les nombres impairs et par conséquent ne se propage pas les nombres impairs jusqu'à ses blocs cibles.  
  
 [!code-cpp[concrt-filter-function#1](../../parallel/concrt/codesnippet/cpp/asynchronous-message-blocks_9.cpp)]  
  
 Cet exemple génère la sortie suivante :  
  
```Output  
0 2 4 6 8  
```  
  
 Une fonction de filtre peut être une fonction lambda, un pointeur de fonction ou un objet de fonction. Chaque fonction de filtre prend l’une des formes suivantes.  
  
```Output  
bool (T)  
bool (T const &)  
```  
  
 Pour éliminer la copie inutile des données, utilisez la deuxième forme lorsque vous avez un type d’agrégation est propagé par valeur.  
  
 Prend en charge le filtrage de message le *flux de données* modèle de programmation, dans lequel les composants exécutent des calculs lorsqu’ils reçoivent des données. Pour obtenir des exemples qui utilisent des fonctions de filtre pour contrôler le flux de données dans un réseau de passage de message, consultez [Comment : utiliser un filtre de bloc de Message](../../parallel/concrt/how-to-use-a-message-block-filter.md), [procédure pas à pas : création d’un Agent de flux de données](../../parallel/concrt/walkthrough-creating-a-dataflow-agent.md), et [ Procédure pas à pas : Création d’un réseau de traitement d’Image](../../parallel/concrt/walkthrough-creating-an-image-processing-network.md).  
  
 [[Haut](#top)]  
  
##  <a name="reservation"></a> Réservation de messages  
 *Réservation de message* permet à un bloc de message de réserver un message pour une utilisation ultérieure. En règle générale, la réservation de messages n’est pas utilisée directement. Toutefois, message de présentation des réservation peut vous aider à mieux comprendre le comportement de certains types de bloc de message prédéfinis.  
  
 Envisagez de jointures non gourmandes et gourmands. Ces deux utilisent la réservation de messages pour réserver des messages pour une utilisation ultérieure. Un décrit précédemment, une jointure non gourmande reçoit des messages en deux phases. Pendant la première phase, non gourmand `join` objet attend que chacune de ses sources de recevoir un message. Une jointure non gourmande tente alors de réserver chacun de ces messages. Si chaque message peut être réservé, elle consomme tous les messages et les propage à sa cible. Dans le cas contraire, il libère, ou annule, les réservations de message et attend une nouvelle fois pour chaque source de recevoir un message.  
  
 Une jointure gourmande, qui lit également les messages d’entrée à partir de plusieurs sources, utilise la réservation de messages pour lire les messages supplémentaires en attendant de recevoir un message de chaque source. Par exemple, considérons une jointure gourmande qui reçoit des messages à partir de blocs de messages `A` et `B`. Si la jointure gourmande reçoit deux messages de B, mais n’a pas encore reçu un message à partir de `A`, la jointure gourmande enregistre l’identificateur unique du message pour le second message à partir de `B`. Une fois la jointure gourmande reçoit un message de `A` et propage ces messages, il utilise l’identificateur de message enregistré pour voir si le deuxième message de `B` est toujours disponible.  
  
 Vous pouvez utiliser la réservation de messages lorsque vous implémentez vos propres types de bloc de message personnalisé. Pour obtenir un exemple sur la création d’un type de bloc de message personnalisé, consultez [procédure pas à pas : création d’un bloc de Message personnalisé](../../parallel/concrt/walkthrough-creating-a-custom-message-block.md).  
  
 [[Haut](#top)]  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)

