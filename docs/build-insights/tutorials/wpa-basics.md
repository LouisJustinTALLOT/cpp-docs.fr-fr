---
title: 'Didacticiel : notions de base de l’analyseur de performances Windows'
description: Didacticiel sur la façon d’effectuer des opérations de base dans l’analyseur de performances Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 2d4473e3682a6e00e0eef61cb73d7450976bcc0c
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91507733"
---
# <a name="tutorial-windows-performance-analyzer-basics"></a>Didacticiel : notions de base de l’analyseur de performances Windows

::: moniker range="<=vs-2017"

Les outils C++ Build Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de **version** de Visual Studio pour cet article sur visual studio 2019. Elle se trouve en haut de la table des matières sur cette page.

::: moniker-end
::: moniker range="vs-2019"

L’utilisation de C++ Build Insights requiert une connaissance de Windows Performance Analyzer (WPA). Cet article vous permet de vous familiariser avec les opérations WPA courantes. Pour plus d’informations sur l’utilisation de WPA, consultez la documentation de l' [Analyseur de performances Windows](/windows-hardware/test/wpt/windows-performance-analyzer) .

## <a name="change-the-view-mode"></a>Modifier le mode d’affichage

WPA offre deux modes d’affichage de base qui vous permettent d’explorer vos traces :

- mode graphique et
- mode table.

Vous pouvez basculer de l’un à l’autre à l’aide des icônes mode d’affichage en haut du volet d’affichage :

![Basculement entre le mode graphique et le mode table.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Sélectionner les présélections

La plupart des affichages WPA de build Insights de C++ vous permettent de choisir parmi plusieurs présélections. Vous pouvez sélectionner la présélection souhaitée à l’aide du menu déroulant en haut du volet d’affichage :

![Sélection d’une présélection.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Zoom avant et arrière

Certains suivis de build sont tellement volumineux qu’il est difficile d’en faire les détails. Pour effectuer un zoom avant sur une zone qui vous intéresse, cliquez avec le bouton droit sur le graphique et sélectionnez **Zoom**. Vous pouvez toujours revenir au paramètre précédent en choisissant annuler le **Zoom**. Cette image montre un exemple d’utilisation d’une sélection et de la commande **Zoom** pour effectuer un zoom avant sur une section du graphique :

![Brève vidéo qui montre comment effectuer un zoom avant sur un graphique.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Regrouper par colonnes différentes

Vous pouvez personnaliser la façon dont votre trace s’affiche. Cliquez sur l’icône d’engrenage en haut du volet d’affichage et réorganisez les colonnes dans l’éditeur de vue de l’Explorateur de builds. Les colonnes se trouvant au-dessus de la ligne jaune dans cette boîte de dialogue sont celles par lesquelles vos lignes de données sont regroupées. La colonne située juste au-dessus de la ligne jaune est spéciale : dans la vue du graphique, elle est affichée sur les barres de couleur.

Cette image montre un exemple de graphique à barres d’un appel de lien. Nous utilisons l’icône d’engrenage pour ouvrir la boîte de dialogue de l’éditeur de vue de l’Explorateur de builds. Ensuite, nous faisons glisser les entrées de colonne de composant et de nom au-dessus de la ligne jaune. La configuration est modifiée pour augmenter le niveau de détail et pour voir ce qui s’est effectivement produit dans l’éditeur de liens :

![Brève vidéo illustrant la façon dont vous pouvez regrouper par colonnes différentes.](media/wpa-grouping.gif)

## <a name="see-also"></a>Voir aussi

[Didacticiel : vcperf et analyseur de performances Windows](vcperf-and-wpa.md)\
[Référence : commandes vcperf](../reference/vcperf-commands.md)\
[Référence : vues de l’analyseur de performances Windows](../reference/wpa-views.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end
