---
description: 'En savoir plus sur : Comment : utiliser la classe Context pour implémenter un sémaphore coopératif'
title: 'Comment : utiliser la classe Context pour implémenter un sémaphore coopératif'
ms.date: 11/04/2016
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
ms.openlocfilehash: d80d364a9dcd27ee7012da5f710d38208c7a9e1c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205653"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Comment : utiliser la classe Context pour implémenter un sémaphore coopératif

Cette rubrique montre comment utiliser la classe Concurrency :: Context pour implémenter une classe de sémaphore coopérative.

## <a name="remarks"></a>Notes

La `Context` classe vous permet de bloquer ou de générer le contexte d’exécution actuel. Le blocage ou le produit du contexte actuel est utile lorsque le contexte actuel ne peut pas continuer, car une ressource n’est pas disponible. Un *sémaphore* est un exemple d’une situation dans laquelle le contexte d’exécution actuel doit attendre qu’une ressource devienne disponible. Un sémaphore, comme un objet de section critique, est un objet de synchronisation qui permet au code d’un contexte d’avoir un accès exclusif à une ressource. Toutefois, contrairement à un objet de section critique, un sémaphore permet à plusieurs contextes d’accéder simultanément à la ressource. Si le nombre maximal de contextes contient un verrou de sémaphore, chaque contexte supplémentaire doit attendre qu’un autre contexte libère le verrou.

### <a name="to-implement-the-semaphore-class"></a>Pour implémenter la classe Semaphore

1. Déclarez une classe nommée `semaphore` . Ajoutez **`public`** des **`private`** sections et à cette classe.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. Dans la **`private`** section de la `semaphore` classe, déclarez une variable [std :: Atomic](../../standard-library/atomic-structure.md) qui contient le nombre de sémaphores et un objet [Concurrency :: concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) qui contient les contextes qui doivent attendre pour acquérir le sémaphore.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. Dans la **`public`** section de la `semaphore` classe, implémentez le constructeur. Le constructeur prend une **`long long`** valeur qui spécifie le nombre maximal de contextes qui peuvent maintenir simultanément le verrou.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. Dans la **`public`** section de la `semaphore` classe, implémentez la `acquire` méthode. Cette méthode décrémente le nombre de sémaphores comme une opération atomique. Si le nombre de sémaphores devient négatif, ajoutez le contexte actuel à la fin de la file d’attente et appelez la méthode [Concurrency :: Context :: Block](reference/context-class.md#block) pour bloquer le contexte actuel.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. Dans la **`public`** section de la `semaphore` classe, implémentez la `release` méthode. Cette méthode incrémente le nombre de sémaphores sous la forme d’une opération atomique. Si le nombre de sémaphores est négatif avant l’opération d’incrémentation, il existe au moins un contexte qui attend le verrou. Dans ce cas, débloquez le contexte qui se trouve au début de la file d’attente.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>Exemple

La `semaphore` classe de cet exemple se comporte de manière coopérative, car `Context::Block` les `Context::Yield` méthodes et produisent l’exécution afin que le runtime puisse exécuter d’autres tâches.

La `acquire` méthode décrémente le compteur, mais il peut ne pas finir d’ajouter le contexte à la file d’attente avant qu’un autre contexte appelle la `release` méthode. Pour tenir compte de cela, la `release` méthode utilise une boucle de spin qui appelle la méthode [Concurrency :: Context :: Yield](reference/context-class.md#yield) pour attendre la fin de l' `acquire` Ajout du contexte par la méthode.

La `release` méthode peut appeler la `Context::Unblock` méthode avant que la `acquire` méthode appelle la `Context::Block` méthode. Vous n’avez pas à vous protéger contre cette condition de concurrence critique, car le runtime permet d’appeler ces méthodes dans n’importe quel ordre. Si la `release` méthode appelle `Context::Unblock` avant que la `acquire` méthode appelle `Context::Block` pour le même contexte, ce contexte reste débloqué. Le runtime requiert uniquement que chaque appel à `Context::Block` soit mis en correspondance avec un appel correspondant à `Context::Unblock` .

L’exemple suivant illustre la `semaphore` classe complète. La `wmain` fonction affiche l’utilisation de base de cette classe. La `wmain` fonction utilise l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour créer plusieurs tâches qui requièrent l’accès au sémaphore. Étant donné que trois threads peuvent maintenir le verrou à tout moment, certaines tâches doivent attendre la fin d’une autre tâche et libérer le verrou.

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

Cet exemple produit l’exemple de sortie suivant.

```Output
In loop iteration 5...
In loop iteration 0...
In loop iteration 6...
In loop iteration 1...
In loop iteration 2...
In loop iteration 7...
In loop iteration 3...
In loop iteration 8...
In loop iteration 9...
In loop iteration 4...
```

Pour plus d’informations sur la `concurrent_queue` classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md). Pour plus d’informations sur l' `parallel_for` algorithme, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `cooperative-semaphore.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Cooperative-Semaphore. cpp**

## <a name="robust-programming"></a>Programmation fiable

Vous pouvez utiliser le modèle RAII ( *Resource Acquisition Is Initialization* ) pour limiter l’accès à un `semaphore` objet à une étendue donnée. Dans le modèle RAII, une structure de données est allouée sur la pile. Cette structure de données Initialise ou acquiert une ressource lors de sa création et détruit ou libère cette ressource lorsque la structure de données est détruite. Le modèle RAII garantit que le destructeur est appelé avant la sortie de la portée englobante. Par conséquent, la ressource est correctement gérée lorsqu’une exception est levée ou lorsqu’une fonction contient plusieurs **`return`** instructions.

L’exemple suivant définit une classe nommée `scoped_lock` , qui est définie dans la **`public`** section de la `semaphore` classe. La `scoped_lock` classe ressemble aux classes [Concurrency :: critical_section :: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) et [concurrency :: reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) . Le constructeur de la `semaphore::scoped_lock` classe acquiert l’accès à l' `semaphore` objet donné et le destructeur libère l’accès à cet objet.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
L’exemple suivant modifie le corps de la fonction de travail qui est passé à l' `parallel_for` algorithme afin qu’il utilise RAII pour s’assurer que le sémaphore est libéré avant le retour de la fonction. Cette technique garantit que la fonction de travail est protégée contre les exceptions.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>Voir aussi

[Contextes](../../parallel/concrt/contexts.md)<br/>
[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)
