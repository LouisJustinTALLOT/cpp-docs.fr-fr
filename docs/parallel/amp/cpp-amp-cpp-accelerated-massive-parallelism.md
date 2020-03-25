---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: c9ef7ab816ec0d17b9dc0b569a6f3a43af83cc68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80167691"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++AMP (C++ Accelerated massive parallelism) accélère l’exécution de votre C++ code en tirant parti du matériel parallèle de données qui est couramment présent en tant qu’unité de traitement graphique (GPU) sur une carte graphique discrète. Le C++ modèle de programmation amp prend en charge les tableaux multidimensionnels, l’indexation, le transfert de mémoire et la mosaïque. Il comprend également une bibliothèque de fonctions mathématiques. Vous pouvez utiliser C++ les extensions de langage amp pour contrôler la façon dont les données sont déplacées du processeur au GPU et inversement.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Décrit les principales fonctionnalités de C++ amp et de la bibliothèque mathématique.|
|[Utilisation de fonctions lambda, d’objets de fonctions et de fonctions restreintes](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Décrit comment utiliser des expressions lambda, des objets de fonction et des fonctions restreintes dans les appels à la méthode [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .|
|[Utilisation des mosaïques](../../parallel/amp/using-tiles.md)|Décrit comment utiliser des vignettes pour accélérer C++ votre code amp.|
|[Utilisation des objets accelerator et accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Décrit comment utiliser des accélérateurs pour personnaliser l’exécution de votre code sur le GPU.|
|[Utilisation de C++ AMP dans les applications UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Décrit comment utiliser C++ les applications AMP dans plateforme Windows universelle (UWP) qui utilisent des types de Windows Runtime.|
|[Graphiques (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Décrit comment utiliser la C++ bibliothèque de graphiques amp.|
|[Procédure pas à pas : multiplication des matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Illustre la multiplication de matrice C++ à l’aide du code amp et de la mosaïque.|
|[Procédure pas-à-pas : débogage d’une application C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explique comment créer et déboguer une application qui utilise la réduction parallèle pour additionner un grand tableau d’entiers.|

## <a name="reference"></a>Informations de référence

[Référence (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static, mot clé](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Autres ressources

[Blog sur la programmation parallèle en code natif](https://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[C++Exemples de projets AMP à télécharger](https://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Analyse C++ du code amp avec le visualiseur concurrentiel](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)
