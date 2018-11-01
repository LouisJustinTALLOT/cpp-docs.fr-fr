---
title: "Comment : utiliser l'annulation pour rompre une boucle parallèle"
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 2a19c2874ce331be2d4f5840f61cabf7bca9abf6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50612743"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Comment : utiliser l'annulation pour rompre une boucle parallèle

Cet exemple montre comment utiliser l’annulation pour implémenter un algorithme de recherche parallèle de base.

## <a name="example"></a>Exemple

L’exemple suivant utilise l’annulation pour rechercher un élément dans un tableau. Le `parallel_find_any` fonction utilise le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme et la [concurrency::run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) (fonction) pour rechercher la position qui contient la valeur donnée. Lorsque la boucle parallèle détecte que la valeur, elle appelle le [Concurrency::cancellation_token_source :: Cancel](reference/cancellation-token-source-class.md#cancel) méthode pour annuler les travaux ultérieurs.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

Le [concurrency::parallel_for](reference/concurrency-namespace-functions.md#parallel_for) algorithme agit simultanément. Par conséquent, il n’effectue pas les opérations dans un ordre prédéterminé. Si le tableau contient plusieurs instances de la valeur, le résultat peut être l’une de ses positions.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio ou collez-le dans un fichier nommé `parallel-array-search.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

**/EHsc CL.exe parallel-array-search.cpp**

## <a name="see-also"></a>Voir aussi

[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for (fonction)](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source, classe](../../parallel/concrt/reference/cancellation-token-source-class.md)
