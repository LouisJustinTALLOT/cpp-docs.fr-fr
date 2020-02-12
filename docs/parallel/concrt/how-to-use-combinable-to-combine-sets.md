---
title: 'Comment : utiliser la classe combinable pour combiner des ensembles'
ms.date: 11/04/2016
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
ms.openlocfilehash: 7ccbb3e8bad5c4d3b6f4177afbfdba3e200681a5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142127"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Comment : utiliser la classe combinable pour combiner des ensembles

Cette rubrique montre comment utiliser la classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) pour calculer le jeu de nombres premiers.

## <a name="example"></a>Exemple

L’exemple suivant calcule le jeu de nombres premiers deux fois. Chaque calcul stocke le résultat dans un objet [std :: BitSet](../../standard-library/bitset-class.md) . L’exemple calcule d’abord le jeu en série, puis calcule le jeu en parallèle. L'exemple affiche également sur la console le temps requis pour effectuer les deux calculs.

Cet exemple utilise l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) et un objet `combinable` pour générer des jeux de threads locaux. Il utilise ensuite la méthode [Concurrency :: combinable :: combine_each](reference/combinable-class.md#combine_each) pour combiner les jeux de threads locaux dans le jeu final.

[!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
serial time: 312 ms

parallel time: 78 ms
```

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-combine-primes.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Parallel-combine-primes. cpp**

## <a name="see-also"></a>Voir aussi

[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)<br/>
[combinable, classe](../../parallel/concrt/reference/combinable-class.md)<br/>
[combinable :: combine_each, méthode](reference/combinable-class.md#combine_each)
