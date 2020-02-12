---
title: 'Procédure pas à pas : implémentation de tâches futures'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 2b9d889dac195bb60651cbb76110d54b6231a5fd
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141979"
---
# <a name="walkthrough-implementing-futures"></a>Procédure pas à pas : implémentation de tâches futures

Cette rubrique montre comment implémenter des futurs dans votre application. La rubrique montre comment combiner les fonctionnalités existantes dans le runtime d’accès concurrentiel dans un autre résultat.

> [!IMPORTANT]
> Cette rubrique illustre le concept de futures à des fins de démonstration. Nous vous recommandons d’utiliser [std :: future](../../standard-library/future-class.md) ou [Concurrency :: Task](../../parallel/concrt/reference/task-class.md) quand vous avez besoin d’une tâche asynchrone qui calcule une valeur pour une utilisation ultérieure.

Une *tâche* est un calcul qui peut être décomposé en calculs supplémentaires, plus précis. Un *futur* est une tâche asynchrone qui calcule une valeur pour une utilisation ultérieure.

Pour implémenter les futures, cette rubrique définit la classe `async_future`. La classe `async_future` utilise ces composants du runtime d’accès concurrentiel : la classe [Concurrency :: task_group](reference/task-group-class.md) et la classe [Concurrency :: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) . La classe `async_future` utilise la classe `task_group` pour calculer une valeur de manière asynchrone et la classe `single_assignment` pour stocker le résultat du calcul. Le constructeur de la classe `async_future` prend une fonction de travail qui calcule le résultat, et la méthode `get` récupère le résultat.

### <a name="to-implement-the-async_future-class"></a>Pour implémenter la classe async_future

1. Déclarez une classe de modèle nommée `async_future` qui est paramétrée sur le type du calcul résultant. Ajoutez `public` sections et `private` à cette classe.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. Dans la section `private` de la classe `async_future`, déclarez un `task_group` et un membre de données `single_assignment`.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. Dans la section `public` de la classe `async_future`, implémentez le constructeur. Le constructeur est un modèle paramétré sur la fonction de travail qui calcule le résultat. Le constructeur exécute de manière asynchrone la fonction de travail dans la `task_group` membre de données et utilise la fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) pour écrire le résultat dans le `single_assignment` membre de données.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. Dans la section `public` de la classe `async_future`, implémentez le destructeur. Le destructeur attend que la tâche se termine.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. Dans la section `public` de la classe `async_future`, implémentez la méthode `get`. Cette méthode utilise la fonction [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) pour récupérer le résultat de la fonction de travail.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant montre l’intégralité de la classe `async_future` et un exemple de son utilisation. La fonction `wmain` crée un objet std ::[Vector](../../standard-library/vector-class.md) qui contient des valeurs entières aléatoires 10 000. Il utilise ensuite `async_future` objets pour rechercher les valeurs les plus petites et les plus grandes contenues dans l’objet `vector`.

### <a name="code"></a>Code

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Commentaires

Cet exemple produit la sortie suivante :

```Output
smallest: 0
largest:  9999
average:  4981
```

L’exemple utilise la méthode `async_future::get` pour récupérer les résultats du calcul. La méthode `async_future::get` attend la fin du calcul si le calcul est toujours actif.

## <a name="robust-programming"></a>Programmation fiable

Pour étendre la classe `async_future` pour gérer les exceptions levées par la fonction de travail, modifiez la méthode `async_future::get` pour appeler la méthode [Concurrency :: task_group :: wait](reference/task-group-class.md#wait) . La méthode `task_group::wait` lève toutes les exceptions générées par la fonction de travail.

L’exemple suivant illustre la version modifiée de la classe `async_future`. La fonction `wmain` utilise un bloc `try`-`catch` pour imprimer le résultat de l’objet `async_future` ou pour imprimer la valeur de l’exception générée par la fonction Work.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Cet exemple produit la sortie suivante :

```Output
caught exception: error
```

Pour plus d’informations sur le modèle de gestion des exceptions dans le runtime d’accès concurrentiel, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `futures.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL. exe/EHsc futures. cpp**

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas relatives au runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Classe task_group](reference/task-group-class.md)<br/>
[single_assignment, classe](../../parallel/concrt/reference/single-assignment-class.md)
