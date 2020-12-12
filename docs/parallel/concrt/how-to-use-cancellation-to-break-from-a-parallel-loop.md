---
description: 'En savoir plus sur : Comment : utiliser l’annulation pour rompre une boucle parallèle'
title: "Comment : utiliser l'annulation pour rompre une boucle parallèle"
ms.date: 11/04/2016
helpviewer_keywords:
- writing a parallel search algorithm [Concurrency Runtime]
- parallel search algorithm, writing [Concurrency Runtime]
ms.assetid: 421cd2de-f058-465f-b890-dd8fcc0df273
ms.openlocfilehash: 0d2817e3a2645cb01d652b7858176ffce6df73c4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97172516"
---
# <a name="how-to-use-cancellation-to-break-from-a-parallel-loop"></a>Comment : utiliser l'annulation pour rompre une boucle parallèle

Cet exemple montre comment utiliser l’annulation pour implémenter un algorithme de recherche parallèle de base.

## <a name="example"></a>Exemple

L’exemple suivant utilise l’annulation pour rechercher un élément dans un tableau. La `parallel_find_any` fonction utilise l’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) et la fonction [concurrency :: run_with_cancellation_token](reference/concurrency-namespace-functions.md#run_with_cancellation_token) pour rechercher la position contenant la valeur donnée. Lorsque la boucle parallèle trouve la valeur, elle appelle la méthode [Concurrency :: cancellation_token_source :: Cancel](reference/cancellation-token-source-class.md#cancel) pour annuler le travail à venir.

[!code-cpp[concrt-parallel-array-search#1](../../parallel/concrt/codesnippet/cpp/how-to-use-cancellation-to-break-from-a-parallel-loop_1.cpp)]

L’algorithme [Concurrency ::p arallel_for](reference/concurrency-namespace-functions.md#parallel_for) agit simultanément. Par conséquent, il n’effectue pas les opérations dans un ordre prédéterminé. Si le tableau contient plusieurs instances de la valeur, le résultat peut être l’une de ses positions.

## <a name="compiling-the-code"></a>Compilation du code

Copiez l’exemple de code et collez-le dans un projet Visual Studio, ou collez-le dans un fichier nommé `parallel-array-search.cpp` , puis exécutez la commande suivante dans une fenêtre d’invite de commandes Visual Studio.

> **cl.exe/EHsc Parallel-Array-Search. cpp**

## <a name="see-also"></a>Voir aussi

[Annulation dans la bibliothèque de modèles parallèles](cancellation-in-the-ppl.md)<br/>
[Algorithmes parallèles](../../parallel/concrt/parallel-algorithms.md)<br/>
[parallel_for, fonction](reference/concurrency-namespace-functions.md#parallel_for)<br/>
[Classe cancellation_token_source](../../parallel/concrt/reference/cancellation-token-source-class.md)
