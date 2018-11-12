---
title: 'Comment : écrire une boucle parallel_for'
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel_for loop [Concurrency Runtime]
- parallel_for function, example
ms.assetid: adb4d64e-5514-4b70-8dcb-b9210e6b5a1c
ms.openlocfilehash: 5caba385304e97bf2e1008a44724c792d56124f5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50592709"
---
# <a name="how-to-write-a-parallelfor-loop"></a>Comment : écrire une boucle parallel_for

Cet exemple montre comment utiliser [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) pour calculer le produit de deux matrices.

## <a name="example"></a>Exemple

L’exemple suivant montre le `matrix_multiply` (fonction), qui calcule le produit de deux matrices carrées.

[!code-cpp[concrt-parallel-matrix-multiply#1](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_1.cpp)]

## <a name="example"></a>Exemple

L’exemple suivant montre le `parallel_matrix_multiply` (fonction), qui utilise le `parallel_for` algorithme pour effectuer la boucle externe en parallèle.

[!code-cpp[concrt-parallel-matrix-multiply#2](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_2.cpp)]

Cet exemple parallélise la boucle externe uniquement car elle exécute suffisamment de travail pour tirer parti de la surcharge de traitement parallèle. Si vous parallélisez la boucle interne, vous recevra pas un gain de performances, car la petite quantité de travail qui exécute la boucle interne ne justifie pas la surcharge de traitement parallèle. Par conséquent, paralléliser uniquement la boucle externe est la meilleure façon d'optimiser les avantages offerts par l'accès concurrentiel sur la plupart des systèmes.

## <a name="example"></a>Exemple

Les éléments suivants exemple plus complet compare les performances de la `matrix_multiply` fonctionner par rapport à la `parallel_matrix_multiply` (fonction).

[!code-cpp[concrt-parallel-matrix-multiply#3](../../parallel/concrt/codesnippet/cpp/how-to-write-a-parallel-for-loop_3.cpp)]

L'exemple de sortie suivant concerne un ordinateur équipé de quatre processeurs.

```Output
serial: 3853
parallel: 1311
```

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-matrix-multiply.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**/EHsc CL.exe parallel-matrix-multiply.cpp**

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for (fonction)](reference/concurrency-namespace-functions.md#parallel_for)

