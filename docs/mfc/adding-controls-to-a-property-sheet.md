---
title: Ajout de contrôles à une feuille de propriétés | Documents Microsoft
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
ms.openlocfilehash: 8437fcdaa04ce7dd2b0a214e4bd3a63ca421d014
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341089"
---
# <a name="adding-controls-to-a-property-sheet"></a>Ajout de contrôles à une feuille de propriétés
Par défaut, une feuille de propriétés alloue de la zone de fenêtre pour les pages de propriétés, l’index de tabulation et les boutons OK, Annuler et appliquer. (Une feuille de propriétés non modale n’a pas du OK, Annuler et appliquer des boutons.) Vous pouvez ajouter d’autres contrôles à la feuille de propriétés. Par exemple, vous pouvez ajouter une fenêtre d’aperçu à droite de la zone de page de propriétés pour afficher les paramètres actuels de l’aspect si appliqué à un objet externe.  
  
 Vous pouvez ajouter des contrôles à la boîte de dialogue de feuille de propriétés dans le `OnCreate` gestionnaire. Insertion de contrôles supplémentaires généralement requiert augmentant la taille de la boîte de dialogue de feuille de propriétés. Après l’appel de la classe de base **CPropertySheet::OnCreate**, appelez [GetWindowRect](../mfc/reference/cwnd-class.md#getwindowrect) pour obtenir la largeur et la hauteur de la fenêtre de feuille de propriétés, développez le rectangle dimensions et appel [MoveWindow](../mfc/reference/cwnd-class.md#movewindow) pour modifier la taille de la fenêtre de feuille de propriétés.  
  
## <a name="see-also"></a>Voir aussi  
 [Feuilles de propriétés](../mfc/property-sheets-mfc.md)   
 [CPropertyPage (classe)](../mfc/reference/cpropertypage-class.md)   
 [CPropertySheet, classe](../mfc/reference/cpropertysheet-class.md)
