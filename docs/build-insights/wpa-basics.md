---
title: 'C++Générer des Insights : notions de base de l’analyseur de performances Windows'
description: Didacticiel sur la façon d’effectuer des opérations de base dans l’analyseur de performances Windows.
ms.date: 11/03/2019
helpviewer_keywords:
- C++ Build Insights
- throughput analysis
- build time analysis
- vcperf.exe
ms.openlocfilehash: 4bd91698561175d876b7a3351a0ed6e85ef73a35
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2019
ms.locfileid: "73633083"
---
# <a name="c-build-insights-windows-performance-analyzer-basics"></a>C++Générer des Insights : notions de base de l’analyseur de performances Windows

::: moniker range="<=vs-2017"

Les C++ outils de génération Insights sont disponibles dans Visual Studio 2019. Pour afficher la documentation de cette version, définissez le contrôle sélecteur de version de Visual Studio pour cet article sur Visual Studio 2019.

::: moniker-end
::: moniker range="vs-2019"

L' C++ utilisation efficace de build Insights requiert une connaissance de l’analyseur de performances Windows (WPA). Cet article vous permet de vous familiariser avec les opérations WPA courantes. Pour plus d’informations sur l’utilisation de WPA, consultez la documentation de l' [Analyseur de performances Windows](/windows-hardware/test/wpt/windows-performance-analyzer) .

## <a name="change-the-view-mode"></a>Modifier le mode d’affichage

WPA offre deux modes d’affichage de base qui vous permettent d’explorer vos traces :

- mode graphique et
- mode table.

Vous pouvez basculer de l’un à l’autre à l’aide des icônes mode d’affichage en haut du volet d’affichage :

![Basculement entre le mode graphique et le mode table.](media/wpa-switching-view-mode.gif)

## <a name="select-presets"></a>Sélectionner les présélections

La C++ plupart des AFFICHAGEs WPA de build Insights offrent plusieurs paramètres prédéfinis que vous pouvez choisir. Vous pouvez sélectionner la présélection souhaitée à l’aide du menu déroulant en haut du volet d’affichage :

![Sélection d’une présélection.](media/wpa-presets.png)

## <a name="zoom-in-and-out"></a>Zoom avant et arrière

Certains suivis de build sont tellement volumineux qu’il est difficile d’en faire les détails. Pour effectuer un zoom avant sur une zone qui vous intéresse, cliquez avec le bouton droit sur le graphique et sélectionnez **Zoom**. Vous pouvez toujours revenir au paramètre précédent en choisissant annuler le **Zoom**. Cette image montre un exemple d’utilisation d’une sélection et de la commande **Zoom** pour effectuer un zoom avant sur une section du graphique :

![Zoom avant sur un graphique.](media/wpa-zooming.gif)

## <a name="group-by-different-columns"></a>Regrouper par colonnes différentes

Vous pouvez personnaliser la façon dont votre trace s’affiche. Cliquez sur l’icône d’engrenage en haut du volet d’affichage et réorganisez les colonnes dans l’éditeur de vue de l’Explorateur de builds. Les colonnes se trouvant au-dessus de la ligne jaune dans cette boîte de dialogue sont celles par lesquelles vos lignes de données sont regroupées. La colonne située juste au-dessus de la ligne jaune est spéciale : dans la vue du graphique, elle est affichée sur les barres de couleur.

Cette image montre un exemple de graphique à barres d’un appel de lien. Nous utilisons l’icône d’engrenage pour ouvrir la boîte de dialogue de l’éditeur de vue de l’Explorateur de builds. Ensuite, nous faisons glisser les entrées de colonne de composant et de nom au-dessus de la ligne jaune. La configuration est modifiée pour augmenter le niveau de détail et pour voir ce qui s’est effectivement produit dans l’éditeur de liens :

![Zoom avant sur un graphique.](media/wpa-grouping.gif)

## <a name="see-also"></a>Voir aussi

[Prise en main C++ de la\ de build Insights](get-started-with-cpp-build-insights.md)
informations de [référence sur vcperf. exe](vcperf-reference.md)\
Informations de référence sur les vues de l' [Analyseur de performances Windows](wpa-views-reference.md)\
[Windows Performance Analyzer](/windows-hardware/test/wpt/windows-performance-analyzer)

::: moniker-end