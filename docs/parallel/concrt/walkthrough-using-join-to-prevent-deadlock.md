---
title: 'Procédure pas à pas : À l’aide de la classe join pour empêcher l’interblocage'
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 196bb4441430c19aa165024e0fc4e42beec6d724
ms.sourcegitcommit: 283cb64fd7958a6b7fbf0cd8534de99ac8d408eb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64857474"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Procédure pas à pas : À l’aide de la classe join pour empêcher l’interblocage

Cette rubrique utilise le problème dîner des philosophes pour illustrer comment utiliser le [concurrency::join](../../parallel/concrt/reference/join-class.md) classe pour empêcher tout interblocage dans votre application. Dans une application logicielle, un *blocage* se produit lorsque au moins deux processus comportent chacun une ressource et attendent mutuellement qu’un autre processus en libère une autre.

Problème dîner des philosophes est un exemple spécifique de l’ensemble général des problèmes qui peuvent se produire lorsqu’un ensemble de ressources est partagé par plusieurs processus simultanés.

## <a name="prerequisites"></a>Prérequis

Lisez les rubriques suivantes avant de commencer cette procédure pas à pas :

- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

- [Procédure pas à pas : création d'une application basée sur des agents](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

- [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)

##  <a name="top"></a> Sections

Cette procédure pas à pas contient les sections suivantes :

- [Problème dîner des philosophes](#problem)

- [Une implémentation Naïve](#deadlock)

- [À l’aide de la classe join pour empêcher l’interblocage](#solution)

##  <a name="problem"></a> Problème dîner des philosophes

Problème dîner des philosophes illustre la façon dont le blocage se produit dans une application. Dans ce problème, cinq philosophes sont assis à une table ronde. Chaque philosophe alterne pense et mange. Chaque philosophe doit partager une baguette avec son voisin de gauche et une autre baguette avec son voisin à droite. L’illustration suivante montre cette disposition.

![Problème dîner des philosophes](../../parallel/concrt/media/dining_philosophersproblem.png "problème dîner des philosophes")

Pour manger, un philosophe doit tenir deux baguettes. Si chaque philosophe tient une seule baguette et attend un autre, puis aucun philosophe ne peut manger et priver les tous.

[[Haut](#top)]

##  <a name="deadlock"></a> Une implémentation Naïve

L’exemple suivant montre une implémentation naïve de problème dîner des philosophes. Le `philosopher` classe qui dérive de [concurrency::agent](../../parallel/concrt/reference/agent-class.md), permet à chaque philosophe agir de façon indépendante. L’exemple utilise un tableau partagé de [concurrency::critical_section](../../parallel/concrt/reference/critical-section-class.md) objets pour accorder à chaque `philosopher` un accès exclusif à une paire de baguettes de l’objet.

Pour l’implémentation à l’illustration, le `philosopher` classe représente un philosophe. Un `int` variable représente chaque baguette. Le `critical_section` objets servent de supports sur lequel reposent les baguettes. Le `run` méthode simule la durée de vie du philosophe. Le `think` méthode simule l’acte de penser et `eat` méthode simule l’acte de manger.

Un `philosopher` objet verrouille les deux `critical_section` objets afin de simuler la suppression des baguettes des supports avant les appels le `eat` (méthode). Après l’appel à `eat`, le `philosopher` objet renvoie des baguettes aux détenteurs en définissant le `critical_section` sauvegarder des objets à l’état déverrouillé.

Le `pickup_chopsticks` illustre la méthode où le blocage peut se produire. Si chaque `philosopher` objet parvient à accéder à un des verrous, puis non `philosopher` objet peut continuer, car l’autre verrou est contrôlé par un autre `philosopher` objet.

## <a name="example"></a>Exemple

### <a name="description"></a>Description

### <a name="code"></a>Code

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `philosophers-deadlock.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**Deadlock.cpp CL.exe /EHsc philosophes**

[[Haut](#top)]

##  <a name="solution"></a> À l’aide de la classe join pour empêcher l’interblocage

Cette section montre comment utiliser des mémoires tampons de messages et des fonctions de passage de message pour éliminer le risque d’interblocage.

Pour lier cet exemple au précédent, le `philosopher` classe remplace chaque `critical_section` objet en utilisant un [concurrency::unbounded_buffer](reference/unbounded-buffer-class.md) objet et un `join` objet. Le `join` objet fait Office d’arbitre qui fournit les baguettes au philosophe.

Cet exemple utilise le `unbounded_buffer` classe, car quand une cible reçoit un message à partir d’un `unbounded_buffer` de l’objet, le message est supprimé de la file d’attente. Cela permet une `unbounded_buffer` objet qui contient un message pour indiquer que la baguette est disponible. Un `unbounded_buffer` objet qui ne conserve aucun message indique que la baguette est utilisée.

Cet exemple utilise un non gourmand `join` de l’objet, car une jointure non gourmande accorde à chacun `philosopher` objet d’accès aux deux baguettes uniquement lorsque les deux `unbounded_buffer` objets contiennent un message. Une jointure gourmande n’empêchera pas de blocage, car une jointure gourmande accepte les messages dès qu’ils deviennent disponibles. Un interblocage peut se produire si tous les gourmand `join` objets reçoivent l’un des messages mais attendent indéfiniment que l’autre devienne disponible.

Pour plus d’informations sur les jointures non gourmandes et et les différences entre les différents types de mémoires tampons de messages, consultez [des blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

#### <a name="to-prevent-deadlock-in-this-example"></a>Pour empêcher tout interblocage dans cet exemple

1. Supprimez le code suivant à partir de l’exemple.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Modifier le type de la `_left` et `_right` membres de données de la `philosopher` classe `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Modifier le `philosopher` constructeur entrent en `unbounded_buffer` objets en tant que ses paramètres.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Modifier le `pickup_chopsticks` méthode à utiliser un non gourmand `join` objet pour recevoir des messages à partir des tampons de messages pour les deux baguettes.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Modifier la `putdown_chopsticks` méthode pour libérer l’accès aux baguettes en envoyant un message aux tampons de messages pour les deux baguettes.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Modifier le `run` méthode pour stocker les résultats de la `pickup_chopsticks` (méthode) et à passer ces résultats à la `putdown_chopsticks` (méthode).

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Modifiez la déclaration de la `chopsticks` variable dans le `wmain` fonction doit être un tableau de `unbounded_buffer` objets qui contiennent chacun un message.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre l’exemple complet qui utilise non gourmand `join` objets pour éliminer le risque d’interblocage.

### <a name="code"></a>Code

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

### <a name="comments"></a>Commentaires

Cet exemple produit la sortie suivante.

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `philosophers-join.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc philosophes-JOIN.cpp**

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)
