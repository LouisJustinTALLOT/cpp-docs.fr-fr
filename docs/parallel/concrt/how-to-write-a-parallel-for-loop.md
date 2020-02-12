---
title: 'Comment : écrire une boucle parallel_for'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 5903114a12de46dc06929c83e9995b39d0136810
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141860"
---
# <a name="how-to-write-a-parallel_for-loop"></a>Comment : écrire une boucle parallel_for

Cet exemple montre comment utiliser l' [accès concurrentiel ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour calculer le produit de deux matrices.

## <a name="example"></a>Exemple

L’exemple suivant illustre la fonction `matrix_multiply`, qui calcule le produit de deux matrices carrées.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant illustre la fonction `parallel_matrix_multiply`, qui utilise l’algorithme `parallel_for` pour effectuer la boucle externe en parallèle.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

Cet exemple parallélise la boucle externe uniquement parce qu’elle effectue suffisamment de travail pour tirer parti de la surcharge liée au traitement parallèle. Si vous paralléliser la boucle interne, vous ne bénéficierez pas d’un gain de performances, car la petite quantité de travail effectuée par la boucle interne ne permet pas de surmonter la surcharge liée au traitement parallèle. Par conséquent, paralléliser uniquement la boucle externe est la meilleure façon d'optimiser les avantages offerts par l'accès concurrentiel sur la plupart des systèmes.

## <a name="example"></a>Exemple

L’exemple plus complet suivant compare les performances de la fonction `matrix_multiply` à la fonction `parallel_matrix_multiply`.

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-matrix-multiply.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc parallel-matrix-multiply. cpp**

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for fonction)](reference/concurrency-namespace-functions.md#parallel_for)
