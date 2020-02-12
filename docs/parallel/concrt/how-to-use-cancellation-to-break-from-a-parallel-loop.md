---
title: "Comment : utiliser l'annulation pour rompre une boucle parallèle"
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 21907de6c5625f7774ae788cef0449ac49107e40
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142131"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Comment : utiliser l'annulation pour rompre une boucle parallèle

Cet exemple montre comment utiliser l’annulation pour implémenter un algorithme de recherche parallèle de base.

## <a name="example"></a>Exemple

L’exemple suivant utilise l’annulation pour rechercher un élément dans un tableau. La fonction `parallel_find_any` utilise l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) et la fonction [Concurrency :: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) pour rechercher la position contenant la valeur donnée. Lorsque la boucle parallèle trouve la valeur, elle appelle la méthode [Concurrency :: cancellation_token_source :: Cancel](reference/cancellation-token-source-class.md#cancel) pour annuler le travail à venir.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

L’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) agit simultanément. Par conséquent, il n’effectue pas les opérations dans un ordre prédéterminé. Si le tableau contient plusieurs instances de la valeur, le résultat peut être l’une de ses positions.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-array-search.cpp` puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **CL. exe/EHsc Parallel-Array-Search. cpp**

## <a name="see-also"></a>Voir aussi

[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for fonction)](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[cancellation_token_source, classe](../../parallel/concrt/reference/cancellation-token-source-class.md)
