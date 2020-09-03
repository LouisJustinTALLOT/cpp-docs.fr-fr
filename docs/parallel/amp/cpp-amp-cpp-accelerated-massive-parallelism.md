---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: 243c476b6536278eb09b26b24becb65276d6e48a
ms.sourcegitcommit: 093f49b8b69daf86661adc125b1d2d7b1f0e0650
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2020
ms.locfileid: "89427632"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism) accélère l’exécution de votre code C++ en tirant parti du matériel parallèle de données qui est couramment présent en tant qu’unité de traitement graphique (GPU) sur une carte graphique discrète. Le modèle de programmation C++ AMP prend en charge les tableaux multidimensionnels, l’indexation, le transfert de mémoire et la mosaïque. Il comprend également une bibliothèque de fonctions mathématiques. Vous pouvez utiliser les extensions de langage C++ AMP pour contrôler la façon dont les données sont déplacées du processeur au GPU et inversement.

## <a name="related-topics"></a>Rubriques connexes

|Intitulé|Description|
|-----------|-----------------|
|[Présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Décrit les principales fonctionnalités de C++ AMP et de la bibliothèque mathématique.|
|[Utilisation des expressions lambda, des objets de fonction et des fonctions restreintes](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Décrit comment utiliser des expressions lambda, des objets de fonction et des fonctions restreintes dans les appels à la méthode [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) .|
|[Utilisation de vignettes](../../parallel/amp/using-tiles.md)|Décrit comment utiliser des vignettes pour accélérer votre code d’C++ AMP.|
|[Utilisation des objets Accelerator et accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Décrit comment utiliser des accélérateurs pour personnaliser l’exécution de votre code sur le GPU.|
|[Utilisation de C++ AMP dans des applications UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Décrit comment utiliser des C++ AMP dans des applications plateforme Windows universelle (UWP) qui utilisent des types de Windows Runtime.|
|[Graphiques (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Décrit comment utiliser la bibliothèque C++ AMP Graphics.|
|[Procédure pas à pas : multiplication des matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Illustre la multiplication de matrice à l’aide d’C++ AMP code et de la mosaïque.|
|[Procédure pas à pas : débogage d’une application C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explique comment créer et déboguer une application qui utilise la réduction parallèle pour additionner un grand tableau d’entiers.|

## <a name="reference"></a>Informations de référence

[Référence (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[Mot clé tile_static](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Autres ressources

[Blog sur la programmation parallèle en code natif](/archive/blogs/nativeconcurrency/)<br/>
[C++ AMP des exemples de projets à télécharger](/archive/blogs/nativeconcurrency/c-amp-sample-projects-for-download)<br/>
[Analyse du code C++ AMP avec le visualiseur concurrentiel](/archive/blogs/nativeconcurrency/analyzing-c-amp-code-with-the-concurrency-visualizer)
