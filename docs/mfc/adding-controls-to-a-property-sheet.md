---
title: Ajout de contrôles à une feuille de propriétés | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0783571ed77d3d8dfaca69edf06330e62d8e98d0
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398496"
---
# <a name="adding-controls-to-a-property-sheet"></a>Ajout de contrôles à une feuille de propriétés

Par défaut, une feuille de propriétés alloue de la zone de fenêtre pour les pages de propriétés, l’index de tabulation et les boutons OK, Annuler et appliquer. (Une feuille de propriétés non modale n’a pas du OK, Annuler et appliquer des boutons.) Vous pouvez ajouter d’autres contrôles à la feuille de propriétés. Par exemple, vous pouvez ajouter une fenêtre d’aperçu vers la droite de la zone de page de propriété pour afficher les paramètres actuels de l’aspect si appliqué à un objet externe pour l’utilisateur.

Vous pouvez ajouter des contrôles à la boîte de dialogue de feuille de propriété dans le `OnCreate` gestionnaire. Insertion de contrôles supplémentaires généralement nécessite augmentant la taille de la boîte de dialogue de feuille de propriété. Après l’appel de la classe de base **CPropertySheet::OnCreate**, appelez [GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect) pour obtenir la largeur et la hauteur de la fenêtre de feuille de propriétés, développez le rectangle dimensions, puis appelez [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) pour modifier la taille de la fenêtre de feuille de propriétés.

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](../mfc/property-sheets-mfc.md)<br/>
[CPropertyPage, classe](../mfc/reference/cpropertypage-class.md)<br/>
[CPropertySheet, classe](../mfc/reference/cpropertysheet-class.md)
