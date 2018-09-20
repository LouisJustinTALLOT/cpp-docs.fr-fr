---
title: 'Comment : exécuter de mappage et réduire les opérations en parallèle | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-concrt
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2eb7580b82d336e3a99d89f6bde6c2f8c950b6c3
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46411298"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Comment : exécuter des opérations de mappage et de réduction en parallèle

Cet exemple montre comment utiliser le [concurrency::parallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) et [concurrency::parallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) algorithmes et les [concurrency::concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)classe pour compter les occurrences de mots dans des fichiers.

Un *carte* opération applique une fonction à chaque valeur dans une séquence. Un *réduire* opération combine les éléments d’une séquence en une seule valeur. Vous pouvez utiliser la bibliothèque Standard C++ [std::transform](../../standard-library/algorithm-functions.md#transform) et [std::accumulate](../../standard-library/numeric-functions.md#accumulate) fonctions pour effectuer le mappage et réduire les opérations. Toutefois, pour améliorer les performances en réponse à de nombreux problèmes, vous pouvez utiliser l'algorithme `parallel_transform` pour effectuer l'opération de mappage en parallèle et l'algorithme `parallel_reduce` pour effectuer l'opération de réduction en parallèle. Dans certains cas, vous pouvez utiliser `concurrent_unordered_map` pour effectuer le mappage et la réduction en une seule opération.

## <a name="example"></a>Exemple

L'exemple suivant compte les occurrences de mots dans des fichiers. Il utilise [std::vector](../../standard-library/vector-class.md) pour représenter le contenu de deux fichiers. L'opération de mappage calcule les occurrences de chaque mot dans chaque vecteur. L'opération de réduction cumule le nombre de mots dans les deux vecteurs.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-map-reduce.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**/EHsc CL.exe parallèle-map-reduce.cpp**

## <a name="robust-programming"></a>Programmation fiable

Dans cet exemple, vous pouvez utiliser la classe `concurrent_unordered_map` (définie dans concurrent_unordered_map.h) pour effectuer le mappage et la réduction en une seule opération.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

En règle générale, vous parallélisez uniquement la boucle externe ou interne. Parallélisez la boucle interne si le nombre de fichiers est relativement petit et que chaque fichier contient beaucoup de mots. Parallélisez la boucle externe si le nombre de fichiers est relativement élevé et que chaque fichier contient peu de mots.

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform, fonction](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce, fonction](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[concurrent_unordered_map, classe](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
