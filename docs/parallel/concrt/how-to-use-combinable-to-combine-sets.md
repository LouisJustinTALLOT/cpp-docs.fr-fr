---
title: 'Comment : utiliser la classe combinable pour combiner des ensembles | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- combinable class, example
- combining sets with combinable [Concurrency Runtime]
ms.assetid: 66ffe8e3-6bbb-4e9f-b790-b612922a68a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 689dacb98bc9f8053686a02414151b4982edca67
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695770"
---
# <a name="how-to-use-combinable-to-combine-sets"></a>Comment : utiliser la classe combinable pour combiner des ensembles
Cette rubrique montre comment utiliser le [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) classe pour calculer le jeu de nombres premiers.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant calcule le jeu de nombres premiers à deux reprises. Chaque calcul stocke le résultat dans un [std::bitset](../../standard-library/bitset-class.md) objet. L’exemple calcule d’abord le jeu en série, puis calcule en parallèle. L'exemple affiche également sur la console le temps requis pour effectuer les deux calculs.  
  
 Cet exemple utilise le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme et un `combinable` objet pour générer des jeux de thread local. Il utilise ensuite la [Concurrency::combinable :: combine_each](reference/combinable-class.md#combine_each) méthode pour combiner les jeux de thread local dans le jeu final.  

  
 [!code-cpp[concrt-parallel-combine-primes#1](../../parallel/concrt/codesnippet/cpp/how-to-use-combinable-to-combine-sets_1.cpp)]  
  
 L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.  
  
```Output  
serial time: 312 ms  
 
parallel time: 78 ms  
```  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-combine-primes.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.  
  
 **/EHsc CL.exe parallel-combine-primes.cpp**  
  
## <a name="see-also"></a>Voir aussi  
 [Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)   
 [combinable (classe)](../../parallel/concrt/reference/combinable-class.md)   
 [combinable::combine_each, méthode](reference/combinable-class.md#combine_each)


