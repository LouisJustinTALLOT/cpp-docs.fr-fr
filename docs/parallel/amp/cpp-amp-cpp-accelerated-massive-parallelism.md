---
title: C++ AMP (C++ Accelerated Massive Parallelism) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- C++ AMP (see C++ Accelerated Massive Parallelism)
- C++ Accelerated Massive Parallelism, getting started
ms.assetid: e27824cb-3167-409b-8c3f-a0e476d8f349
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98ae6b6a5cd24a1ea146cca7ccb30fcbdc93ae75
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2018
ms.locfileid: "33705365"
---
# <a name="c-amp-c-accelerated-massive-parallelism"></a>C++ AMP (C++ Accelerated Massive Parallelism)
C++ AMP (C++ Accelerated Massive Parallelism) accélère l’exécution de votre code C++ en tirant parti du matériel parallèle de données qui est généralement présent sous la forme d’une unité de traitement graphique (GPU) sur une carte graphique distincte. Le modèle de programmation C++ AMP prend en charge les tableaux multidimensionnels, l’indexation, le transfert de la mémoire et l’affichage en mosaïque. Il inclut également une bibliothèque de fonctions mathématiques. Vous pouvez utiliser les extensions de langage C++ AMP pour contrôler la façon dont les données sont déplacées à partir de l’UC vers le GPU et sauvegarder.  
  
## <a name="related-topics"></a>Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Présentation de C++ AMP](../../parallel/amp/cpp-amp-overview.md)|Décrit les principales fonctionnalités de C++ AMP et la bibliothèque mathématique.|  
|[Utilisation de fonctions lambda, d’objets de fonctions et de fonctions restreintes](../../parallel/amp/using-lambdas-function-objects-and-restricted-functions.md)|Décrit comment utiliser des expressions lambda, objets de fonction et de fonctions restreintes dans les appels à la [parallel_for_each](reference/concurrency-namespace-functions-amp.md#parallel_for_each) (méthode).|  
|[Utilisation des mosaïques](../../parallel/amp/using-tiles.md)|Décrit comment utiliser des vignettes pour accélérer votre code C++ AMP.|  
|[Utilisation des objets accelerator et accelerator_view](../../parallel/amp/using-accelerator-and-accelerator-view-objects.md)|Décrit comment utiliser des accélérateurs pour personnaliser l’exécution de votre code sur le GPU.|  
|[Utilisation de C++ AMP dans les applications UWP](../../parallel/amp/using-cpp-amp-in-windows-store-apps.md)|Décrit comment utiliser C++ AMP dans les applications de plateforme Windows universelle (UWP) qui utilisent des types Windows Runtime.|  
|[Graphiques (C++ AMP)](../../parallel/amp/graphics-cpp-amp.md)|Décrit comment utiliser la bibliothèque de graphiques de C++ AMP.|  
|[Procédure pas à pas : multiplication des matrices](../../parallel/amp/walkthrough-matrix-multiplication.md)|Montre la multiplication des matrices à l’aide de code C++ AMP et mettre en mosaïque.|  
|[Procédure pas-à-pas : débogage d’une application C++ AMP](../../parallel/amp/walkthrough-debugging-a-cpp-amp-application.md)|Explique comment créer et déboguer une application qui utilise la réduction parallèle à cumuler un grand tableau d’entiers.|  
  
## <a name="reference"></a>Référence  
 [Référence (C++ AMP)](../../parallel/amp/reference/reference-cpp-amp.md)  
  
 [tile_static, mot clé](../../cpp/tile-static-keyword.md)  
  
 [restrict (C++ AMP)](../../cpp/restrict-cpp-amp.md)  
  
## <a name="other-resources"></a>Autres ressources  
 [Programmation parallèle dans le Blog de Code natif](http://go.microsoft.com/fwlink/p/?linkid=238472)  
  
 [Exemples de projets C++ AMP pour le téléchargement](http://go.microsoft.com/fwlink/p/?linkid=248508)  
  
 [Analyse du Code C++ AMP avec le visualiseur concurrentiel](http://go.microsoft.com/fwlink/p/?linkid=253987&clcid=0x409)

