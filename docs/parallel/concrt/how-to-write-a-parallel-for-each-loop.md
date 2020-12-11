---
description: 'En savoir plus sur : Comment : écrire une boucle de parallel_for_each'
title: 'Comment : écrire une boucle parallel_for_each'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for_each loop [Concurrency Runtime]
- parallel_for_each function, example
ms.assetid: fa9c0ba6-ace0-4f88-8681-c7c1f52aff20
ms.openlocfilehash: cb80173d3d4c78fe4d46f017d60af2c3c6659096
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97112230"
---
# <a name="how-to-write-a-parallel_for_each-loop"></a>Comment : écrire une boucle parallel_for_each

Cet exemple montre comment utiliser l’algorithme d' [accès concurrentiel ::p arallel_for_each](reference/concurrency-namespace-functions.md#parallel_for_each) pour calculer le nombre de nombres premiers dans un objet [std :: Array](../../standard-library/array-class-stl.md) en parallèle.

## <a name="example"></a>Exemple

L’exemple suivant calcule le nombre de nombres premiers dans un tableau deux fois. L’exemple utilise tout d’abord l’algorithme [std :: for_each](../../standard-library/algorithm-functions.md#for_each) pour calculer le nombre en série. L’exemple utilise ensuite l' `parallel_for_each` algorithme pour effectuer la même tâche en parallèle. L'exemple affiche également sur la console le temps requis pour effectuer les deux calculs.

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

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-count-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Parallel-count-primes. cpp**

## <a name="robust-programming"></a>Programmation fiable

L’expression lambda que l’exemple passe à l' `parallel_for_each` algorithme utilise la `InterlockedIncrement` fonction pour permettre aux itérations parallèles de la boucle d’incrémenter le compteur simultanément. Si vous utilisez des fonctions telles que `InterlockedIncrement` pour synchroniser l’accès aux ressources partagées, vous pouvez présenter des goulots d’étranglement au niveau des performances dans votre code. Vous pouvez utiliser un mécanisme de synchronisation sans verrou, par exemple la classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) , pour éliminer l’accès simultané aux ressources partagées. Pour obtenir un exemple qui utilise la `combinable` classe de cette manière, consultez [Comment : utiliser combinable pour améliorer les performances](../../parallel/concrt/how-to-use-combinable-to-improve-performance.md).

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for_each, fonction](reference/concurrency-namespace-functions.md#parallel_for_each)
