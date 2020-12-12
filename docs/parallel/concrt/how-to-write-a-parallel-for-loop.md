---
description: 'En savoir plus sur : Comment : écrire une boucle de parallel_for'
title: 'Comment : écrire une boucle parallel_for'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: ccf66c3e457b540721f0a76722b9d17206cf0f7f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97205692"
---
# <a name="how-to-write-a-parallel_for-loop"></a>Comment : écrire une boucle parallel_for

Cet exemple montre comment utiliser l' [accès concurrentiel ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour calculer le produit de deux matrices.

## <a name="example-compute-the-product-of-two-matrices"></a>Exemple : calculer le produit de deux matrices

L’exemple suivant illustre la `matrix_multiply` fonction, qui calcule le produit de deux matrices carrées.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example-compute-a-matrix-multiply-in-parallel"></a>Exemple : calculer une matrice multiplier en parallèle

L’exemple suivant illustre la `parallel_matrix_multiply` fonction, qui utilise l' `parallel_for` algorithme pour effectuer la boucle externe en parallèle.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

Cet exemple parallélise la boucle externe uniquement parce qu’elle effectue suffisamment de travail pour tirer parti de la surcharge liée au traitement parallèle. Si vous paralléliser la boucle interne, vous ne bénéficierez pas d’un gain de performances, car la petite quantité de travail effectuée par la boucle interne ne permet pas de surmonter la surcharge liée au traitement parallèle. Par conséquent, paralléliser uniquement la boucle externe est la meilleure façon d'optimiser les avantages offerts par l'accès concurrentiel sur la plupart des systèmes.

## <a name="example-finished-parallel_for-loop-code-sample"></a>Exemple : fini parallel_for exemple de code de boucle

L’exemple plus complet suivant compare les performances de la `matrix_multiply` fonction par rapport à la `parallel_matrix_multiply` fonction.

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-matrix-multiply.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc parallel-matrix-multiply. cpp**

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for, fonction](reference/concurrency-namespace-functions.md#parallel_for)
