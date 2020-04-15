---
title: 'Tutorial: Windows Performance Analyzer basics'
description: Tutoriel sur la façon de compléter les opérations de base dans Windows Performance Analyzer.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: ae1050b9389527a12f5bdbea6d695c0f20510127
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81323400"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Tutorial: Windows Performance Analyzer basics

::: moniker range="<=vs-2017"

Les outils build Insights sont disponibles dans Visual Studio 2019. Pour voir la documentation de cette version, définissez le contrôle du sélecteur Visual Studio **Version** pour cet article à Visual Studio 2019. On le trouve en haut de la table des contenus sur cette page.

::: moniker-end
::: moniker range="vs-2019"

L’utilisation efficace de L’utilisation de L’insights build de CMD nécessite une certaine connaissance de Windows Performance Analyzer (WPA). Cet article vous aide à vous familiariser avec les opérations communes de WPA. Pour plus d’informations sur la façon d’utiliser WPA, consultez la documentation [de Windows Performance Analyzer.](/windows-hardware/test/wpt/windows-performance-analyzer)

## <a name="change-the-view-mode"></a>Modifier le mode de vue

WPA offre deux modes de vue de base pour vous d’explorer vos traces:

- mode graphique, et
- mode table.

Vous pouvez basculer entre eux en utilisant les icônes de mode de vue en haut de la vitre de vue :

![Passer du mode graphique au mode table.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Sélectionnez des préréglages

La plupart des vues WPA Build Insights de CMD ont plusieurs presets à choisir. Vous pouvez sélectionner le préréglage que vous souhaitez en utilisant le menu drop-down en haut de la vitre de vue:

![Sélection d’un préréglage.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Zoom sur et hors

Certaines traces de construction sont si grandes qu’il est difficile de faire ressortir les détails. Pour zoomer sur une zone qui vous intéresse, cliquez à droite sur le graphique et sélectionnez **Zoom**. Vous pouvez toujours revenir au paramètre précédent en choisissant **Undo Zoom**. Cette image montre un exemple d’utilisation d’une sélection et de la commande **Zoom** pour zoomer sur une section du graphique :

![Zoom sur un graphique.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Groupe par différentes colonnes

Vous pouvez personnaliser la façon dont votre trace est affichée. Cliquez sur l’icône de l’engrenage en haut d’une vitre et réorganisez les colonnes de l’éditeur Build Explorer View. Les colonnes trouvées au-dessus de la ligne jaune dans ce dialogue sont ceux que vos lignes de données sont regroupées par. La colonne juste au-dessus de la ligne jaune est spéciale: dans la vue graphique, elle est affichée sur les barres colorées.

Cette image montre un graphique à barres d’exemple d’une invocation de lien. Nous utilisons l’icône de l’engrenage pour ouvrir le dialogue Build Explorer View Editor. Ensuite, nous faisons glisser les entrées de la colonne composant et nom au-dessus de la ligne jaune. La configuration est modifiée pour augmenter le niveau de détail, et pour voir ce qui s’est réellement passé à l’intérieur du lien:

![Zoom sur un graphique.](media/wpa-grouping.gif)

## <a name="see-also"></a>Voir aussi

[Tutorial: vcperf et Windows Performance Analyzer](vcperf-and-wpa.md)\
[Référence: commandes de vcperf](/cpp/build-insights/reference/vcperf-commands)\
[Référence: Vues d’analyseur de performance Windows](/cpp/build-insights/reference/wpa-views)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
