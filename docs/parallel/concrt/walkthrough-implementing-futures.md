---
title: 'Procédure pas à pas : implémentation d’objets future'
ms.date: 04/25/2019
helpviewer_keywords:
- implementing futures [Concurrency Runtime]
- futures, implementing [Concurrency Runtime]
ms.assetid: 82ea75cc-aaec-4452-b10d-8abce0a87e5b
ms.openlocfilehash: 9bf46b7f2a761aaf0c07e1017524c8ddf533aca6
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230296"
---
# <a name="walkthrough-implementing-futures"></a>Procédure pas à pas : implémentation d’objets future

Cette rubrique montre comment implémenter des futurs dans votre application. La rubrique montre comment combiner les fonctionnalités existantes dans le runtime d’accès concurrentiel dans un autre résultat.

> [!IMPORTANT]
> Cette rubrique illustre le concept de futures à des fins de démonstration. Nous vous recommandons d’utiliser [std :: future](../../standard-library/future-class.md) ou [Concurrency :: Task](../../parallel/concrt/reference/task-class.md) quand vous avez besoin d’une tâche asynchrone qui calcule une valeur pour une utilisation ultérieure.

Une *tâche* est un calcul qui peut être décomposé en calculs supplémentaires, plus précis. Un *futur* est une tâche asynchrone qui calcule une valeur pour une utilisation ultérieure.

Pour implémenter les futures, cette rubrique définit la `async_future` classe. La `async_future` classe utilise ces composants du runtime d’accès concurrentiel : la classe [Concurrency :: task_group](reference/task-group-class.md) et la classe [concurrency :: single_assignment](../../parallel/concrt/reference/single-assignment-class.md) . La `async_future` classe utilise la `task_group` classe pour calculer une valeur de façon asynchrone et la `single_assignment` classe pour stocker le résultat du calcul. Le constructeur de la `async_future` classe prend une fonction de travail qui calcule le résultat, et la `get` méthode récupère le résultat.

### <a name="to-implement-the-async_future-class"></a>Pour implémenter la classe async_future

1. Déclarez une classe de modèle nommée `async_future` qui est paramétrable sur le type du calcul résultant. Ajoutez **`public`** des **`private`** sections et à cette classe.

[!code-cpp[concrt-futures#2](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_1.cpp)]

1. Dans la **`private`** section de la `async_future` classe, déclarez un `task_group` et un `single_assignment` membre de données.

[!code-cpp[concrt-futures#3](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_2.cpp)]

1. Dans la **`public`** section de la `async_future` classe, implémentez le constructeur. Le constructeur est un modèle paramétré sur la fonction de travail qui calcule le résultat. Le constructeur exécute de manière asynchrone la fonction de travail dans le `task_group` membre de données et utilise la fonction [Concurrency :: Send](reference/concurrency-namespace-functions.md#send) pour écrire le résultat dans le `single_assignment` membre de données.

[!code-cpp[concrt-futures#4](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_3.cpp)]

1. Dans la **`public`** section de la `async_future` classe, implémentez le destructeur. Le destructeur attend que la tâche se termine.

[!code-cpp[concrt-futures#5](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_4.cpp)]

1. Dans la **`public`** section de la `async_future` classe, implémentez la `get` méthode. Cette méthode utilise la fonction [Concurrency :: Receive](reference/concurrency-namespace-functions.md#receive) pour récupérer le résultat de la fonction de travail.

[!code-cpp[concrt-futures#6](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_5.cpp)]

## <a name="example"></a>Exemple

### <a name="description"></a>Description

L’exemple suivant illustre la `async_future` classe complète et un exemple de son utilisation. La `wmain` fonction crée un objet std ::[Vector](../../standard-library/vector-class.md) qui contient des valeurs entières aléatoires 10 000. Il utilise ensuite des `async_future` objets pour rechercher les plus petites et les plus grandes valeurs contenues dans l' `vector` objet.

### <a name="code"></a>Code

[!code-cpp[concrt-futures#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_6.cpp)]

### <a name="comments"></a>Commentaires

Cet exemple produit la sortie suivante :

```Output
smallest: 0
largest:  9999
average:  4981
```

L’exemple utilise la `async_future::get` méthode pour récupérer les résultats du calcul. La `async_future::get` méthode attend que le calcul se termine si le calcul est toujours actif.

## <a name="robust-programming"></a>Programmation fiable

Pour étendre la `async_future` classe afin de gérer les exceptions levées par la fonction de travail, modifiez la `async_future::get` méthode pour appeler la méthode [Concurrency :: task_group :: wait](reference/task-group-class.md#wait) . La `task_group::wait` méthode lève toutes les exceptions générées par la fonction de travail.

L’exemple suivant illustre la version modifiée de la `async_future` classe. La `wmain` fonction utilise un **`try`** - **`catch`** bloc pour imprimer le résultat de l' `async_future` objet ou pour imprimer la valeur de l’exception générée par la fonction de travail.

[!code-cpp[concrt-futures-with-eh#1](../../parallel/concrt/codesnippet/cpp/walkthrough-implementing-futures_7.cpp)]

Cet exemple produit la sortie suivante :

```Output
caught exception: error
```

Pour plus d’informations sur le modèle de gestion des exceptions dans le runtime d’accès concurrentiel, consultez [gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `futures.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**cl.exe/EHsc futures. cpp**

## <a name="see-also"></a>Voir aussi

[Procédures pas à pas runtime d’accès concurrentiel](../../parallel/concrt/concurrency-runtime-walkthroughs.md)<br/>
[Gestion des exceptions](../../parallel/concrt/exception-handling-in-the-concurrency-runtime.md)<br/>
[Classe task_group](reference/task-group-class.md)<br/>
[Classe single_assignment](../../parallel/concrt/reference/single-assignment-class.md)
