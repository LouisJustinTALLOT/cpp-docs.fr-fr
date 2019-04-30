---
title: Pages et feuilles de propriétés dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: fa8ee3518ad2b32e0eace77f0961eb86ccde1822
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391372"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Pages et feuilles de propriétés dans MFC

Une feuille de propriétés, également appelé une boîte de dialogue tab, est une boîte de dialogue qui contient les pages de propriétés. Chaque page de propriétés est basé sur une ressource de modèle de boîte de dialogue et contient des contrôles. Il est placé sur une page avec un onglet en haut. L’onglet noms de la page et indique son objectif. Les utilisateurs cliquent sur un onglet dans la feuille de propriétés pour sélectionner un ensemble de contrôles.

Utilisez les pages pour regrouper les contrôles dans la feuille de propriétés dans des jeux explicites. La feuille de propriétés de relation contenant-contenu a généralement plusieurs contrôles qui lui sont propres. Elles s’appliquent à toutes les pages.

Feuilles de propriétés sont basés sur la classe [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Pages de propriétés sont basés sur la classe [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Une feuille de propriétés est un type spécial de la boîte de dialogue qui est généralement utilisée pour modifier les attributs d’un objet externe, telles que la sélection actuelle dans une vue. La feuille de propriétés a trois parties principales : la boîte de dialogue contenant des pages de propriétés d’un ou plusieurs celui illustré à la fois et un onglet en haut de chaque page que l’utilisateur clique pour sélectionner cette page. Feuilles de propriétés sont utiles pour les cas où vous disposez de plusieurs groupes similaires des options pour modifier ou de paramètres. Une feuille de propriétés regroupe les informations d’une manière facilement compréhensible.

> [!NOTE]
>  Lorsque vous essayez d’afficher une feuille de propriétés à l’aide de `CPropertySheet::DoModal`, le système peut générer une exception de première chance. Cette exception se produit, car le système tente de modifier le [Styles de fenêtre](../mfc/reference/styles-used-by-mfc.md#window-styles) de l’objet avant de l’objet a été créé. Pour plus d’informations sur cette exception et également comment l’éviter ou de gérer, consultez [CPropertySheet::DoModal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](../mfc/property-sheets-mfc.md)
