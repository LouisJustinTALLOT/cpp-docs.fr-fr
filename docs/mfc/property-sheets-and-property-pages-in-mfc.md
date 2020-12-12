---
description: En savoir plus sur les feuilles de propriétés et les pages de propriétés dans MFC
title: Pages et feuilles de propriétés dans MFC
ms.date: 11/04/2016
helpviewer_keywords:
- property pages [MFC], MFC
- controls [MFC], property sheets
- property sheets, MFC
- tab dialog boxes
ms.assetid: e1bede2b-0285-4b88-a052-0f8a372807a2
ms.openlocfilehash: 93662dcf07e2810ad9f4f51d6df8341f9f6df6dc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97185425"
---
# <a name="property-sheets-and-property-pages-in-mfc"></a>Pages et feuilles de propriétés dans MFC

Une feuille de propriétés, également appelée boîte de dialogue à onglets, est une boîte de dialogue qui contient les pages de propriétés. Chaque page de propriétés est basée sur une ressource de modèle de boîte de dialogue et contient des contrôles. Elle est placée sur une page avec un onglet en haut. L’onglet nomme la page et indique son objectif. Les utilisateurs cliquent sur un onglet de la feuille de propriétés pour sélectionner un ensemble de contrôles.

Utilisez des pages pour regrouper les contrôles de la feuille de propriétés dans des ensembles significatifs. La feuille de propriétés contenue a généralement plusieurs contrôles propres. Elles s’appliquent à toutes les pages.

Les feuilles de propriétés sont basées sur la classe [CPropertySheet](../mfc/reference/cpropertysheet-class.md). Les pages de propriétés sont basées sur la classe [CPropertyPage](../mfc/reference/cpropertypage-class.md).

Une feuille de propriétés est un type spécial de boîte de dialogue qui est généralement utilisé pour modifier les attributs d’un objet externe, tel que la sélection actuelle dans une vue. La feuille de propriétés comporte trois parties principales : la boîte de dialogue conteneur, une ou plusieurs pages de propriétés affichées une par une, et un onglet en haut de chaque page sur laquelle l’utilisateur clique pour sélectionner cette page. Les feuilles de propriétés sont utiles dans les situations où vous pouvez modifier plusieurs groupes similaires de paramètres ou d’options. Une feuille de propriétés regroupe les informations de manière facile à comprendre.

> [!NOTE]
> Lorsque vous essayez d’afficher une feuille de propriétés à l’aide de `CPropertySheet::DoModal` , le système peut générer une exception de première chance. Cette exception se produit car le système tente de modifier les [styles de fenêtre](../mfc/reference/styles-used-by-mfc.md#window-styles) de l’objet avant la création de l’objet. Pour plus d’informations sur cette exception et sur la façon de l’éviter ou de la gérer, consultez [CPropertySheet ::D omodal](../mfc/reference/cpropertysheet-class.md#domodal).

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](../mfc/property-sheets-mfc.md)
