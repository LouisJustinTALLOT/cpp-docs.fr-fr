---
description: 'En savoir plus sur : Comment : effectuer des opérations de mappage et de réduction en parallèle'
title: 'Comment : exécuter des opérations de mappage et de réduction en parallèle'
ms.date: 11/04/2016
helpviewer_keywords:
- parallel_transform function, example
- parallel map and reduce, example
- parallel_reduce function, example
ms.assetid: 9d19fac0-4ab6-4380-a375-3b18eeb87720
ms.openlocfilehash: f35c9bf4df5a79cf9568bc286ff628e2f9fd45c1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97209839"
---
# <a name="how-to-perform-map-and-reduce-operations-in-parallel"></a>Comment : exécuter des opérations de mappage et de réduction en parallèle

Cet exemple montre comment utiliser les algorithmes d' [accès concurrentiel ::p arallel_transform](reference/concurrency-namespace-functions.md#parallel_transform) et d' [accès concurrentiel ::p arallel_reduce](reference/concurrency-namespace-functions.md#parallel_reduce) et la classe [Concurrency :: concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md) pour compter les occurrences des mots dans les fichiers.

Une opération de *mappage* applique une fonction à chaque valeur d’une séquence. Une opération de *réduction* combine les éléments d’une séquence en une seule valeur. Vous pouvez utiliser les fonctions de la bibliothèque standard C++ [std :: Transform](../../standard-library/algorithm-functions.md#transform) et [std :: Accumulate](../../standard-library/numeric-functions.md#accumulate) pour effectuer des opérations de mappage et de réduction. Toutefois, pour améliorer les performances en réponse à de nombreux problèmes, vous pouvez utiliser l'algorithme `parallel_transform` pour effectuer l'opération de mappage en parallèle et l'algorithme `parallel_reduce` pour effectuer l'opération de réduction en parallèle. Dans certains cas, vous pouvez utiliser `concurrent_unordered_map` pour effectuer le mappage et la réduction en une seule opération.

## <a name="example"></a>Exemple

L'exemple suivant compte les occurrences de mots dans des fichiers. Elle utilise [std :: Vector](../../standard-library/vector-class.md) pour représenter le contenu de deux fichiers. L'opération de mappage calcule les occurrences de chaque mot dans chaque vecteur. L'opération de réduction cumule le nombre de mots dans les deux vecteurs.

[!code-cpp[concrt-parallel-map-reduce#1](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_1.cpp)]

## <a name="compiling-the-code"></a>Compilation du code

Pour compiler le code, copiez-le, puis collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-map-reduce.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Parallel-Map-Reduce. cpp**

## <a name="robust-programming"></a>Programmation fiable

Dans cet exemple, vous pouvez utiliser la classe `concurrent_unordered_map` (définie dans concurrent_unordered_map.h) pour effectuer le mappage et la réduction en une seule opération.

[!code-cpp[concrt-parallel-map-reduce#2](../../parallel/concrt/codesnippet/cpp/how-to-perform-map-and-reduce-operations-in-parallel_2.cpp)]

En règle générale, vous parallélisez uniquement la boucle externe ou interne. Parallélisez la boucle interne si le nombre de fichiers est relativement petit et que chaque fichier contient beaucoup de mots. Parallélisez la boucle externe si le nombre de fichiers est relativement élevé et que chaque fichier contient peu de mots.

## <a name="see-also"></a>Voir aussi

[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_transform, fonction](reference/concurrency-namespace-functions.md#parallel_transform)<br/>
[parallel_reduce fonction)](reference/concurrency-namespace-functions.md#parallel_reduce)<br/>
[Classe concurrent_unordered_map](../../parallel/concrt/reference/concurrent-unordered-map-class.md)
