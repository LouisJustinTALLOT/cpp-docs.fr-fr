---
title: 'Comment : écrire une boucle parallel_for_each'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: e3b19ec180f9f4e75a2f280a0ecd159e5b932565
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50610507"
---
# <a name="how-to-write-a-parallelforeach-loop"></a>Comment : écrire une boucle parallel_for_each

Cet exemple montre comment utiliser le [concurrency::parallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) algorithme pour calculer le nombre de nombres premiers dans un [std::array](../../standard-library/array-class-stl.md) objet en parallèle.

## <a name="example"></a>Exemple

L’exemple suivant calcule le nombre de nombres premiers dans un tableau à deux reprises. L’exemple utilise d’abord la [std::for_each](../../standard-library/algorithm-functions.md#for_each) algorithme pour calculer le nombre en série. L’exemple utilise ensuite la `parallel_for_each` algorithme pour effectuer la même tâche en parallèle. L'exemple affiche également sur la console le temps requis pour effectuer les deux calculs.

[!code-cpp[concrt-parallel-count-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-each-loop_1.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
serial version:
found 17984 prime numbers
took 6115 ms

parallel version:
found 17984 prime numbers
took 1653 ms
```

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-count-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**/EHsc CL.exe parallel-count-primes.cpp**

## <a name="robust-programming"></a>Programmation fiable

L’expression lambda que l’exemple passe à la `parallel_for_each` algorithme utilise le `InterlockedIncrement` (fonction) pour permettre aux itérations parallèles de la boucle d’incrémenter le compteur simultanément. Si vous utilisez des fonctions telles que `InterlockedIncrement` pour synchroniser l’accès aux ressources partagées, vous pouvez présenter les goulots d’étranglement dans votre code. Vous pouvez utiliser un mécanisme de synchronisation sans verrou, par exemple, le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) (classe), pour éliminer l’accès simultané aux ressources partagées. Pour obtenir un exemple qui utilise le `combinable` de classe de cette manière, consultez [Comment : utiliser la classe combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each, fonction](reference/concurrency-namespace-functions.md#parallel_for_each)

