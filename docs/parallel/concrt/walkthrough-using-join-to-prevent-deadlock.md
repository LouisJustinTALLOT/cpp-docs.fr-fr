---
title: "Procédure pas à pas : utilisation de la classe join pour empêcher l'interblocage"
ms.date: 04/25/2019
helpviewer_keywords:
- preventing deadlock with joins [Concurrency Runtime]
- deadlock, preventing [Concurrency Runtime]
- non-greedy joins, example
- join class, example
ms.assetid: d791f697-bb93-463e-84bd-5df1651b7446
ms.openlocfilehash: 4df83e944552fd6c0d2482efa72883d87cd45f8c
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140656"
---
# <a name="walkthrough-using-join-to-prevent-deadlock"></a>Procédure pas à pas : utilisation de la classe join pour empêcher l'interblocage

Cette rubrique utilise le problème du dîner de philosophes pour illustrer comment utiliser la classe [Concurrency :: Join](../../parallel/concrt/reference/join-class.md) pour empêcher tout interblocage dans votre application. Dans une application logicielle, un *blocage* se produit lorsque au moins deux processus comportent chacun une ressource et attendent mutuellement qu’un autre processus en libère une autre.

Le problème du dîner de philosophes est un exemple spécifique de l’ensemble général de problèmes qui peuvent se produire lorsqu’un ensemble de ressources est partagé entre plusieurs processus simultanés.

## <a name="prerequisites"></a>Conditions préalables requises

Lisez les rubriques suivantes avant de commencer cette procédure pas à pas :

- [Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)

- [Procédure pas à pas : création d’une application basée sur un agent](../../parallel/concrt/walkthrough-creating-an-agent-based-application.md)

- [Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)

- [Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)

- [Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)

## <a name="top"></a> Sections

Cette procédure pas à pas contient les sections suivantes :

- [Problème du dîner de philosophes](#problem)

- [Implémentation naïve](#deadlock)

- [Utilisation de Join pour empêcher l’interblocage](#solution)

## <a name="problem"></a>Problème du dîner de philosophes

Le problème du dîner de philosophes illustre la manière dont le blocage se produit dans une application. Dans ce problème, cinq philosophes se trouvent dans une table ronde. Chaque philosophe alterne entre la pensée et le manger. Chaque philosophe doit partager une baguette avec le voisin à gauche et une autre baguette avec le voisin à droite. L’illustration suivante montre cette disposition.

![Problème du dîner de philosophes](../../parallel/concrt/media/dining_philosophersproblem.png "Problème Dîner des philosophes")

Pour manger, un philosophe doit contenir deux baguettes. Si chaque philosophe contient une seule baguette et attend un autre, aucun philosophe ne peut manger et tout le détriment.

[[Haut](#top)]

## <a name="deadlock"></a>Implémentation naïve

L’exemple suivant montre une implémentation naïve du problème du dîner de philosophes. La classe `philosopher`, qui dérive de [Concurrency :: agent](../../parallel/concrt/reference/agent-class.md), permet à chaque philosophe d’agir indépendamment. L’exemple utilise un tableau partagé d’objets [Concurrency :: critical_section](../../parallel/concrt/reference/critical-section-class.md) pour octroyer à chaque `philosopher` un accès exclusif à une paire de baguettes.

Pour associer l’implémentation à l’illustration, la classe `philosopher` représente un philosophe. Une variable `int` représente chaque baguette. Les objets `critical_section` jouent le rôle de conteneurs sur lesquels les baguettes restantes. La méthode `run` simule la vie du philosophe. La méthode `think` simule l’acte de pensée et la méthode `eat` simule l’acte de manger.

Un objet `philosopher` verrouille les deux objets `critical_section` pour simuler la suppression des baguettes des détenteurs avant d’appeler la méthode `eat`. Après l’appel à `eat`, l’objet `philosopher` retourne les baguettes aux titulaires en affectant à la `critical_section` les objets l’État déverrouillé.

La méthode `pickup_chopsticks` illustre l’endroit où un blocage peut se produire. Si chaque objet `philosopher` accède à l’un des verrous, aucun objet `philosopher` ne peut continuer, car l’autre verrou est contrôlé par un autre objet `philosopher`.

### <a name="example"></a>Exemple

[!code-cpp[concrt-philosophers-deadlock#1](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_1.cpp)]

### <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `philosophers-deadlock.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Philosophers-Deadlock. cpp**

[[Haut](#top)]

## <a name="solution"></a>Utilisation de Join pour empêcher l’interblocage

Cette section montre comment utiliser des mémoires tampons de messages et des fonctions de passage de messages pour éliminer le risque d’interblocage.

Pour associer cet exemple à l’exemple précédent, la classe `philosopher` remplace chaque objet `critical_section` à l’aide d’un objet [Concurrency :: unbounded_buffer](reference/unbounded-buffer-class.md) et d’un objet `join`. L’objet `join` sert d’arbitre qui fournit les baguettes au philosophe.

Cet exemple utilise la classe `unbounded_buffer`, car lorsqu’une cible reçoit un message d’un objet `unbounded_buffer`, le message est supprimé de la file d’attente de messages. Cela permet à un objet `unbounded_buffer` qui contient un message d’indiquer que la baguette est disponible. Un objet `unbounded_buffer` qui ne contient aucun message indique que la baguette est utilisée.

Cet exemple utilise un objet `join` non gourmand, car une jointure non gourmande donne à chaque `philosopher` l’accès aux deux baguettes uniquement lorsque les deux objets `unbounded_buffer` contiennent un message. Une jointure gourmande n’empêche pas le blocage, car une jointure gourmande accepte des messages dès qu’ils sont disponibles. Un blocage peut se produire si tous les objets gourmands en `join` reçoivent l’un des messages, mais attendent indéfiniment que l’autre soit disponible.

Pour plus d’informations sur les jointures gourmandes et non gourmandes, ainsi que sur les différences entre les différents types de tampons de messages, consultez [blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md).

### <a name="to-prevent-deadlock-in-this-example"></a>Pour éviter les verrous mortels dans cet exemple

1. Supprimez le code suivant de l’exemple.

[!code-cpp[concrt-philosophers-deadlock#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_2.cpp)]

1. Modifiez le type de la `_left` et `_right` membres de données de la classe `philosopher` en `unbounded_buffer`.

[!code-cpp[concrt-philosophers-join#2](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_3.cpp)]

1. Modifiez le constructeur `philosopher` pour qu’il prenne `unbounded_buffer` objets comme paramètres.

[!code-cpp[concrt-philosophers-join#3](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_4.cpp)]

1. Modifiez la méthode `pickup_chopsticks` pour utiliser un objet `join` non gourmand pour recevoir des messages à partir des tampons de messages pour les deux baguettes.

[!code-cpp[concrt-philosophers-join#4](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_5.cpp)]

1. Modifiez la méthode `putdown_chopsticks` pour libérer l’accès aux baguettes en envoyant un message aux tampons de messages pour les deux baguettes.

[!code-cpp[concrt-philosophers-join#5](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_6.cpp)]

1. Modifiez la méthode `run` pour conserver les résultats de la méthode `pickup_chopsticks` et passer ces résultats à la méthode `putdown_chopsticks`.

[!code-cpp[concrt-philosophers-join#6](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_7.cpp)]

1. Modifiez la déclaration de la variable `chopsticks` dans la fonction `wmain` pour qu’elle soit un tableau d’objets `unbounded_buffer` qui contiennent chacun un message.

[!code-cpp[concrt-philosophers-join#7](../../parallel/concrt/codesnippet/cpp/walkthrough-using-join-to-prevent-deadlock_8.cpp)]

### <a name="description"></a>Description

Le code suivant illustre l’exemple complet qui utilise des objets `join` non gourmands pour éliminer le risque d’interblocage.

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

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `philosophers-join.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Philosophers-Join. cpp**

[[Haut](#top)]

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Bibliothèque d’agents asynchrones](../../parallel/concrt/asynchronous-agents-library.md)<br/>
[Agents asynchrones](../../parallel/concrt/asynchronous-agents.md)<br/>
[Blocs de messages asynchrones](../../parallel/concrt/asynchronous-message-blocks.md)<br/>
[Fonctions de passage de messages](../../parallel/concrt/message-passing-functions.md)<br/>
[Structures de données de synchronisation](../../parallel/concrt/synchronization-data-structures.md)
