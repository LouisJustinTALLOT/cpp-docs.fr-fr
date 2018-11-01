---
title: C++ AMP (C++ Accelerated Massive Parallelism)
ms.date: 11/04/2016
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
ms.openlocfilehash: f8ac71023f66868a66fb8c54a5e86678225378a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613172"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)

C++ AMP (C++ Accelerated Massive Parallelism) accélère l’exécution de votre code C++ en tirant parti du matériel parallèle de données qui est plus communément présent en tant qu’une unité de traitement graphique (GPU) sur une carte graphique distincte. Le modèle de programmation C++ AMP inclut la prise en charge pour les tableaux multidimensionnels, l’indexation, le transfert de la mémoire et de la mosaïque. Il inclut également une bibliothèque de fonctions mathématiques. Vous pouvez utiliser des extensions de langage C++ AMP pour contrôler la façon dont les données sont déplacées à partir de l’UC au GPU et le sauvegarder.

## <a name="related-topics"></a>Rubriques connexes

|Titre|Description|
|-----------|-----------------|
|[Présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Décrit les principales fonctionnalités de C++ AMP et de la bibliothèque mathématique.|
|[Utilisation de fonctions lambda, d’objets de fonctions et de fonctions restreintes](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Décrit comment utiliser des expressions lambda, des objets de fonction et des fonctions restreintes dans les appels à la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) (méthode).|
|[Utilisation des mosaïques](../../parallel/amp/using-tiles.md)|Décrit comment utiliser les mosaïques pour accélérer votre code C++ AMP.|
|[Utilisation des objets accelerator et accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Décrit comment utiliser des accélérateurs pour personnaliser l’exécution de votre code sur le GPU.|
|[Utilisation de C++ AMP dans les applications UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Décrit comment utiliser C++ AMP dans les applications de plateforme universelle Windows (UWP) qui utilisent des types Windows Runtime.|
|[Graphiques (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Décrit comment utiliser la bibliothèque de graphiques de C++ AMP.|
|[Procédure pas à pas : multiplication des matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Montre une multiplication de matrice à l’aide de code C++ AMP et de la mosaïque.|
|[Procédure pas-à-pas : débogage d’une application C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explique comment créer et déboguer une application qui utilise la réduction parallèle pour résumer un grand tableau d’entiers.|

## <a name="reference"></a>Référence

[Référence (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)<br/>
[tile_static, mot clé](../../cpp/tile-static-keyword.md)<br/>
[restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)

## <a name="other-resources"></a>Autres ressources

[Programmation parallèle en Code natif Blog](http://go.microsoft.com/fwlink/p/?linkid=238472)<br/>
[Exemples de projets C++ AMP pour téléchargement](http://go.microsoft.com/fwlink/p/?linkid=248508)<br/>
[Analyse du Code C++ AMP avec le visualiseur concurrentiel](https://blogs.msdn.microsoft.com/nativeconcurrency/2012/03/09/analyzing-c-amp-code-with-the-concurrency-visualizer/)