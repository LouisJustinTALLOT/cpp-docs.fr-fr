---
title: 'Comment : utiliser la classe Context pour implémenter un sémaphore coopératif | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- cooperative semaphore implementing
- context class
ms.assetid: 22f4b9c0-ca22-4a68-90ba-39e99ea76696
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 384fe7674ff24af0250dede7cb4bafda0106bf46
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46424779"
---
# <a name="how-to-use-the-context-class-to-implement-a-cooperative-semaphore"></a>Comment : utiliser la classe Context pour implémenter un sémaphore coopératif

Cette rubrique montre comment utiliser la classe concurrency::Context d’implémenter une classe de sémaphore coopératif.

Le `Context` classe vous permet de bloquer ou de céder le contexte d’exécution actuel. Blocage ou la cession le contexte actuel est utile lorsque le contexte actuel ne peut pas continuer car une ressource n’est pas disponible. Un *sémaphore* est un exemple de situation où le contexte d’exécution actuel doit attendre qu’une ressource devienne disponible. Un sémaphore, comme un objet de section critique, est un objet de synchronisation qui permet au code dans un contexte de disposer d’un accès exclusif à une ressource. Toutefois, contrairement à un objet de section critique, un sémaphore permet à plusieurs contextes d’accéder à la ressource simultanément. Si le nombre maximal de contextes détient un verrou de sémaphore, chaque contexte supplémentaire doit attendre un autre contexte libérer le verrou.

### <a name="to-implement-the-semaphore-class"></a>Pour implémenter la classe semaphore

1. Déclarez une classe nommée `semaphore`. Ajouter `public` et `private` sections à cette classe.

[!code-cpp[concrt-cooperative-semaphore#1](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_1.cpp)]

1. Dans le `private` section de la `semaphore` classe, déclarez un [std::atomic](../../standard-library/atomic-structure.md) variable qui contient le compteur du sémaphore et un [concurrency::concurrent_queue](../../parallel/concrt/reference/concurrent-queue-class.md) objet qui contient les contextes qui doit attendre pour acquérir le sémaphore.

[!code-cpp[concrt-cooperative-semaphore#2](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_2.cpp)]

1. Dans le `public` section de la `semaphore` classe, implémentez le constructeur. Le constructeur accepte un `long long` valeur qui spécifie le nombre maximal de contextes qui peuvent détenir simultanément le verrou.

[!code-cpp[concrt-cooperative-semaphore#3](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_3.cpp)]

1. Dans le `public` section de la `semaphore` classe, implémentez la `acquire` (méthode). Cette méthode décrémente le nombre de sémaphores comme une opération atomique. Si le compteur du sémaphore devient négatif, ajoutez le contexte actuel à la fin de la file d’attente et appelez le [Concurrency::Context :: Block](reference/context-class.md#block) méthode pour bloquer le contexte actuel.

[!code-cpp[concrt-cooperative-semaphore#4](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_4.cpp)]

1. Dans le `public` section de la `semaphore` classe, implémentez la `release` (méthode). Cette méthode incrémente le compteur du sémaphore comme une opération atomique. Si le compteur du sémaphore est négatif avant l’opération d’incrément, il est au moins un contexte qui attend le verrou. Dans ce cas, débloquez le contexte qui se trouve au début de la file d’attente.

[!code-cpp[concrt-cooperative-semaphore#5](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_5.cpp)]

## <a name="example"></a>Exemple

Le `semaphore` classe dans cet exemple se comporte de manière coopérative, car le `Context::Block` et `Context::Yield` méthodes suspendent l’exécution afin que le runtime peut effectuer d’autres tâches.

Le `acquire` méthode décrémente le compteur, mais elle risque de ne pas avoir fini d’ajouter le contexte à la file d’attente avant qu’un autre contexte appelle le `release` (méthode). Pour prendre en compte pour ce faire, le `release` méthode utilise une boucle de rotation qui appelle le [Concurrency::Context :: yield](reference/context-class.md#yield) méthode pour attendre la `acquire` méthode pour terminer l’ajout du contexte.

Le `release` méthode peut appeler le `Context::Unblock` méthode avant le `acquire` les appels de méthode le `Context::Block` (méthode). Il est inutile pour vous protéger contre cette condition de concurrence, car le runtime permet à ces méthodes à appeler dans n’importe quel ordre. Si le `release` les appels de méthode `Context::Unblock` avant la `acquire` les appels de méthode `Context::Block` pour le même contexte, ce contexte reste non bloqué. Le runtime exige uniquement que chaque appel à `Context::Block` est mis en correspondance avec un appel correspondant à `Context::Unblock`.

L’exemple suivant montre l’ensemble `semaphore` classe. Le `wmain` fonction montre l’utilisation de cette classe de base. Le `wmain` fonction utilise le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme afin de créer plusieurs tâches qui requièrent l’accès au sémaphore. Étant donné que trois threads peuvent contenir le verrou à tout moment, certaines tâches doivent attendre une autre tâche se termine et libère le verrou.

[!code-cpp[concrt-cooperative-semaphore#6](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_6.cpp)]

Cet exemple produit la sortie suivante.

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

Pour plus d’informations sur la `concurrent_queue` de classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md). Pour plus d’informations sur la `parallel_for` algorithme, consultez [algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `cooperative-semaphore.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc cooperative-semaphore.cpp**

## <a name="robust-programming"></a>Programmation fiable

Vous pouvez utiliser la *Resource Acquisition Is Initialization* modèle (RAII) pour limiter l’accès à un `semaphore` objet à une portée donnée. Dans le modèle RAII, une structure de données est allouée sur la pile. Cette structure de données initialise ou acquiert une ressource lorsqu’il est créé et détruit ou libère cette ressource lorsque la structure de données est détruite. Le modèle RAII garantit que le destructeur est appelé avant la fermeture de la portée englobante. Par conséquent, la ressource est gérée correctement lorsqu’une exception est levée ou lorsqu’une fonction contient plusieurs `return` instructions.

L’exemple suivant définit une classe nommée `scoped_lock`, qui est défini dans le `public` section de la `semaphore` classe. Le `scoped_lock` classe est similaire à la [Concurrency::critical_section :: scoped_lock](reference/critical-section-class.md#critical_section__scoped_lock_class) et [Concurrency::reader_writer_lock :: scoped_lock](reference/reader-writer-lock-class.md#scoped_lock_class) classes. Le constructeur de la `semaphore::scoped_lock` classe acquiert l’accès à la donnée `semaphore` objet et le destructeur libère l’accès à cet objet.

[!code-cpp[concrt-cooperative-semaphore#7](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_7.cpp)]
L’exemple suivant modifie le corps de la fonction de travail qui est passé à la `parallel_for` algorithme afin qu’elle utilise le modèle RAII pour s’assurer que le sémaphore est libéré avant le retour de la fonction. Cette technique garantit que la fonction de travail est protégé contre les exceptions.

[!code-cpp[concrt-cooperative-semaphore#8](../../parallel/concrt/codesnippet/cpp/how-to-use-the-context-class-to-implement-a-cooperative-semaphore_8.cpp)]

## <a name="see-also"></a>Voir aussi

[Contextes](../../parallel/concrt/contexts.md)<br/>
[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)

