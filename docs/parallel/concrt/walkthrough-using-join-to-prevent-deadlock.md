---
title: 'Procédure pas à pas : utilisation de la classe join pour empêcher l’interblocage'
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 5bdd6cd81051d224714dd66d4604cbdec4ddb552
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87217881"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Procédure pas à pas : utilisation de la classe join pour empêcher l’interblocage

Cette rubrique utilise le problème du dîner de philosophes pour illustrer comment utiliser la classe [Concurrency :: Join](../../parallel/concrt/reference/join-class.md) pour empêcher tout interblocage dans votre application. Dans une application logicielle, un *blocage* se produit lorsque au moins deux processus comportent chacun une ressource et attendent mutuellement qu’un autre processus en libère une autre.

Le problème du dîner de philosophes est un exemple spécifique de l’ensemble général de problèmes qui peuvent se produire lorsqu’un ensemble de ressources est partagé entre plusieurs processus simultanés.

## <a name="prerequisites"></a>Prérequis

Lisez les rubriques suivantes avant de commencer cette procédure pas à pas :

- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

- [Procédure pas à pas : création d’une application basée sur un agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

- [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)

## <a name="sections"></a><a name="top"></a>Sections

Cette procédure pas à pas contient les sections suivantes :

- [Problème Dîner des philosophes](#problem)

- [Implémentation naïve](#deadlock)

- [Utilisation de Join pour empêcher l’interblocage](#solution)

## <a name="the-dining-philosophers-problem"></a><a name="problem"></a>Problème du dîner de philosophes

Le problème du dîner de philosophes illustre la manière dont le blocage se produit dans une application. Dans ce problème, cinq philosophes se trouvent dans une table ronde. Chaque philosophe alterne entre la pensée et le manger. Chaque philosophe doit partager une baguette avec le voisin à gauche et une autre baguette avec le voisin à droite. L’illustration suivante montre cette disposition.

![Problème Dîner des philosophes](../../parallel/concrt/media/dining_philosophersproblem.png "Problème Dîner des philosophes")

Pour manger, un philosophe doit contenir deux baguettes. Si chaque philosophe contient une seule baguette et attend un autre, aucun philosophe ne peut manger et tout le détriment.

[[Haut](#top)]

## <a name="a-nave-implementation"></a><a name="deadlock"></a>Implémentation naïve

L’exemple suivant montre une implémentation naïve du problème du dîner de philosophes. La `philosopher` classe, qui dérive de [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md), permet à chaque philosophe d’agir indépendamment. L’exemple utilise un tableau partagé d’objets [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md) pour octroyer à chaque `philosopher` objet un accès exclusif à une paire de baguettes.

Pour associer l’implémentation à l’illustration, la `philosopher` classe représente un philosophe. Une **`int`** variable représente chaque baguette. Les `critical_section` objets servent de conteneurs sur lesquels le reste des baguettes. La `run` méthode simule la vie du philosophe. La `think` méthode simule l’acte de pensée et la `eat` méthode simule l’acte de manger.

Un `philosopher` objet verrouille les deux `critical_section` objets pour simuler la suppression des baguettes des détenteurs avant d’appeler la `eat` méthode. Après l’appel à `eat` , l' `philosopher` objet retourne les baguettes aux titulaires en redéfinissant les `critical_section` objets à l’État déverrouillé.

La `pickup_chopsticks` méthode illustre l’endroit où un blocage peut se produire. Si chaque `philosopher` objet accède à l’un des verrous, aucun `philosopher` objet ne peut continuer, car l’autre verrou est contrôlé par un autre `philosopher` objet.

### <a name="example"></a>Exemple

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

### <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `philosophers-deadlock.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Philosophers-Deadlock. cpp**

[[Haut](#top)]

## <a name="using-join-to-prevent-deadlock"></a><a name="solution"></a>Utilisation de Join pour empêcher l’interblocage

Cette section montre comment utiliser des mémoires tampons de messages et des fonctions de passage de messages pour éliminer le risque d’interblocage.

Pour associer cet exemple à l’exemple précédent, la `philosopher` classe remplace chaque `critical_section` objet à l’aide d’un objet [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) et d’un `join` objet. L' `join` objet sert d’arbitre qui fournit les baguettes au philosophe.

Cet exemple utilise la `unbounded_buffer` classe, car lorsqu’une cible reçoit un message d’un `unbounded_buffer` objet, le message est supprimé de la file d’attente de messages. Cela permet `unbounded_buffer` à un objet qui contient un message d’indiquer que la baguette est disponible. Un `unbounded_buffer` objet qui ne contient aucun message indique que la baguette est utilisée.

Cet exemple utilise un objet non gourmand `join` , car une jointure non gourmande donne `philosopher` à chaque objet l’accès aux deux baguettes uniquement lorsque les deux `unbounded_buffer` objets contiennent un message. Une jointure gourmande n’empêche pas le blocage, car une jointure gourmande accepte des messages dès qu’ils sont disponibles. Un blocage peut se produire si tous les objets gourmands `join` reçoivent l’un des messages, mais attendent indéfiniment que l’autre soit disponible.

Pour plus d’informations sur les jointures gourmandes et non gourmandes, ainsi que sur les différences entre les différents types de tampons de messages, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="to-prevent-deadlock-in-this-example"></a>Pour éviter les verrous mortels dans cet exemple

1. Supprimez le code suivant de l’exemple.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Remplacez le type des `_left` `_right` données membres et de la `philosopher` classe par `unbounded_buffer` .

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Modifiez le `philosopher` constructeur pour qu’il prenne des `unbounded_buffer` objets comme ses paramètres.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Modifiez la `pickup_chopsticks` méthode pour utiliser un objet qui n’est pas gourmand `join` pour recevoir des messages des tampons de messages pour les deux baguettes.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Modifiez la `putdown_chopsticks` méthode pour libérer l’accès aux baguettes en envoyant un message aux tampons de messages pour les deux baguettes.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Modifiez la `run` méthode de façon à conserver les résultats de la `pickup_chopsticks` méthode et à passer ces résultats à la `putdown_chopsticks` méthode.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Modifiez la déclaration de la `chopsticks` variable dans la `wmain` fonction pour qu’elle soit un tableau d' `unbounded_buffer` objets qui contiennent chacun un message.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

### <a name="description"></a>Description

Le code suivant illustre l’exemple complet qui utilise des objets non gourmands `join` pour éliminer le risque d’interblocage.

### <a name="example"></a>Exemple

[!code-cpp[concrt-philosophers-join#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_9.cpp)]

Cet exemple produit la sortie suivante.

```Output
aristotle ate 50 times.
descartes ate 50 times.
hobbes ate 50 times.
socrates ate 50 times.
plato ate 50 times.
```

### <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `philosophers-join.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Philosophers-Join. cpp**

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)
