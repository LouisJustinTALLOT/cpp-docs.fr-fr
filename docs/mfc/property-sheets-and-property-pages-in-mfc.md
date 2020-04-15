---
title: Pages et feuilles de propriétés dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 10fb34c79745e672d30dd2d3c3b97d457583f795
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371172"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Pages et feuilles de propriétés dans MFC

Une feuille de propriété, également connue sous le nom de boîte de dialogue d’onglet, est une boîte de dialogue qui contient des pages de propriété. Chaque page de propriété est basée sur une ressource de modèle de dialogue et contient des contrôles. Il est clos sur une page avec un onglet sur le dessus. L’onglet nomme la page et indique son but. Les utilisateurs cliquent sur un onglet dans la feuille de propriété pour sélectionner un ensemble de contrôles.

Utilisez des pages pour regrouper les contrôles de la feuille de propriété en ensembles significatifs. La feuille de propriété contenue a généralement plusieurs contrôles de ses propres. Celles-ci s’appliquent à toutes les pages.

Les feuilles de propriété sont basées sur la classe [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Les pages de propriété sont basées sur la classe [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Une feuille de propriété est un type spécial de boîte de dialogue qui est généralement utilisé pour modifier les attributs d’un objet externe, comme la sélection actuelle dans une vue. La feuille de propriété comporte trois parties principales : la boîte de dialogue contenant, une ou plusieurs pages de propriété affichées une à la fois, et un onglet en haut de chaque page que l’utilisateur clique pour sélectionner cette page. Les feuilles de propriété sont utiles pour les situations où vous avez plusieurs groupes similaires de paramètres ou d’options à changer. Une feuille de propriété regroupe l’information d’une manière facile à comprendre.

> [!NOTE]
> Lorsque vous essayez de montrer une `CPropertySheet::DoModal`feuille de propriété en utilisant, le système peut générer une exception de première chance. Cette exception se produit parce que le système essaie de changer les styles de [fenêtre](../mfc/reference/styles-used-by-mfc.md#window-styles) de l’objet avant que l’objet a été créé. Pour plus d’informations sur cette exception, et aussi comment l’éviter ou la manipuler, voir [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Voir aussi

[Feuilles de propriété](../mfc/property-sheets-mfc.md)
