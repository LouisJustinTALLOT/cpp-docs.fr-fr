---
title: 'Comment : convertir une boucle OpenMP qui a recours à une variable de réduction pour utiliser le runtime d’accès concurrentiel'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: b58f6025c41091b39375c566d2c1d4b4798437b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50633075"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Comment : convertir une boucle OpenMP qui a recours à une variable de réduction pour utiliser le runtime d’accès concurrentiel

Cet exemple montre comment convertir une OpenMP [parallèles](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[pour](../../parallel/openmp/reference/for-openmp.md) boucle qui utilise le [réduction](../../parallel/openmp/reference/reduction.md) clause pour utiliser le Runtime d’accès concurrentiel.

Le OpenMP `reduction` clause vous permet de spécifier une ou plusieurs variables de thread privé qui font l’objet d’une opération de réduction à la fin de la région parallèle. OpenMP prédéfinit un ensemble d’opérateurs de réduction. Chaque variable de réduction doit être une valeur scalaire (par exemple, `int`, `long`, et `float`). OpenMP définit également plusieurs restrictions sur l’utilisation des variables de réduction dans une région parallèle.

La bibliothèque de modèles parallèles (PPL) fournit la [concurrency::combinable](../../parallel/concrt/reference/combinable-class.md) classe, qui fournit un stockage local des threads réutilisable qui vous permet d’effectuer des calculs affinés puis de fusionner ces calculs dans finale résultat. Le `combinable` classe est un modèle qui agit sur les types scalaires et complexes. Pour utiliser le `combinable` classe, exécuter des sous-calculs dans le corps d’une construction parallèle, puis appelez le [Concurrency::combinable :: combine](reference/combinable-class.md#combine) ou [Concurrency::combinable :: combine_each](reference/combinable-class.md#combine_each) méthode pour produire le résultat final. Le `combine` et `combine_each` méthodes chaque prennent un *combiner fonction* qui spécifie comment combiner chaque paire d’éléments. Par conséquent, la `combinable` classe n’est pas limitée à un ensemble fixe d’opérateurs de réduction.

## <a name="example"></a>Exemple

Cet exemple utilise OpenMP et le Runtime d’accès concurrentiel pour calculer la somme des nombres de Fibonacci tout d’abord 35.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

Pour plus d’informations sur la `combinable` de classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `concrt-omp-fibonacci-reduction.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**CL.exe /EHsc/OpenMP concrt-omp-fibonacci-reduction.cpp**

## <a name="see-also"></a>Voir aussi

[Migration d’OpenMP au runtime d’accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)

