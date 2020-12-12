---
description: 'En savoir plus sur : Comment : convertir une boucle OpenMP qui utilise une variable de réduction pour utiliser le runtime d’accès concurrentiel'
title: 'Comment : convertir une boucle OpenMP qui a recours à une variable de réduction pour utiliser le runtime d’accès concurrentiel'
ms.date: 11/04/2016
helpviewer_keywords:
- converting from OpenMP to the Concurrency Runtime, reduction variables
- reduction variables, converting from OpenMP to the Concurrency Runtime
ms.assetid: 96623f36-5e57-4d3f-8c13-669e6cd535b1
ms.openlocfilehash: 131585caf3e06a11ed45bda4b58efa541272006f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97325756"
---
# <a name="how-to-convert-an-openmp-loop-that-uses-a-reduction-variable-to-use-the-concurrency-runtime"></a>Comment : convertir une boucle OpenMP qui a recours à une variable de réduction pour utiliser le runtime d’accès concurrentiel

Cet exemple montre comment convertir une boucle OpenMP [Parallel](../../parallel/concrt/how-to-use-parallel-invoke-to-write-a-parallel-sort-routine.md#parallel)[for](../openmp/reference/openmp-directives.md#for-openmp) qui utilise la clause [reduction](../openmp/reference/openmp-clauses.md#reduction) pour utiliser l’Runtime d’accès concurrentiel.

La `reduction` clause OpenMP vous permet de spécifier une ou plusieurs variables privées du thread qui sont soumises à une opération de réduction à la fin de la région parallèle. OpenMP prédéfinit un ensemble d’opérateurs de réduction. Chaque variable de réduction doit être scalaire (par exemple, **`int`** , **`long`** et **`float`** ). OpenMP définit également plusieurs restrictions sur la façon dont les variables de réduction sont utilisées dans une région parallèle.

La bibliothèque de modèles parallèles (PPL) fournit la classe [Concurrency :: combinable](../../parallel/concrt/reference/combinable-class.md) , qui fournit un stockage local des threads réutilisable qui vous permet d’effectuer des calculs affinés, puis de fusionner ces calculs dans un résultat final. La `combinable` classe est un modèle qui agit à la fois sur des types scalaires et complexes. Pour utiliser la `combinable` classe, effectuez des sous-calculs dans le corps d’une construction parallèle, puis appelez la méthode [Concurrency :: combinable :: combine](reference/combinable-class.md#combine) ou [Concurrency :: combinable :: combine_each](reference/combinable-class.md#combine_each) pour produire le résultat final. Les `combine` `combine_each` méthodes et prennent chacune une *fonction combine* qui spécifie comment combiner chaque paire d’éléments. Par conséquent, la `combinable` classe n’est pas limitée à un ensemble fixe d’opérateurs de réduction.

## <a name="example"></a>Exemple

Cet exemple utilise à la fois OpenMP et le runtime d’accès concurrentiel pour calculer la somme des 35 premiers nombres de Fibonacci.

[!code-cpp[concrt-openmp#7](../../parallel/concrt/codesnippet/cpp/convert-an-openmp-loop-that-uses-a-reduction-variable_1.cpp)]

Cet exemple produit la sortie suivante.

```Output
Using OpenMP...
The sum of the first 35 Fibonacci numbers is 14930351.
Using the Concurrency Runtime...
The sum of the first 35 Fibonacci numbers is 14930351.
```

Pour plus d’informations sur la `combinable` classe, consultez [conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md).

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `concrt-omp-fibonacci-reduction.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc/OpenMP concrt-omp-fibonacci-reduction. cpp**

## <a name="see-also"></a>Voir aussi

[Migration d'OpenMP au runtime d'accès concurrentiel](../../parallel/concrt/migrating-from-openmp-to-the-concurrency-runtime.md)<br/>
[Conteneurs et objets parallèles](../../parallel/concrt/parallel-containers-and-objects.md)
