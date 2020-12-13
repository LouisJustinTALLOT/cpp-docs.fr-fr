---
description: 'En savoir plus sur : ajout de contrôles à une feuille de propriétés'
title: Ajout de contrôles à une feuille de propriétés
ms.date: 11/04/2016
helpviewer_keywords:
- controls [MFC], adding to property sheets
- property sheets, adding controls
ms.assetid: 24ad4c0b-c1db-4850-b9f0-34aae8d74571
ms.openlocfilehash: e220d08b46f1db7e09ad1f1398731ce7a98f2dc5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97339074"
---
# <a name="adding-controls-to-a-property-sheet"></a>Ajout de contrôles à une feuille de propriétés

Par défaut, une feuille de propriétés alloue la zone de fenêtre pour les pages de propriétés, l’index de tabulation et les boutons OK, annuler et appliquer. (Une feuille de propriétés non modale n’a pas les boutons OK, annuler et appliquer.) Vous pouvez ajouter d’autres contrôles à la feuille de propriétés. Par exemple, vous pouvez ajouter une fenêtre d’aperçu à droite de la zone de la page de propriétés pour indiquer à l’utilisateur à quoi ressemblerait les paramètres actuels s’ils sont appliqués à un objet externe.

Vous pouvez ajouter des contrôles à la boîte de dialogue de la feuille de propriétés dans le `OnCreate` Gestionnaire. L’adaptation de contrôles supplémentaires nécessite généralement l’augmentation de la taille de la boîte de dialogue de la feuille de propriétés. Après l’appel de la classe de base **CPropertySheet :: OnCreate**, appelez [GetWindowRect](reference/cwnd-class.md#getwindowrect) pour connaître la largeur et la hauteur de la fenêtre de la feuille de propriétés actuellement allouée, développez les dimensions du rectangle, puis appelez [MoveWindow](reference/cwnd-class.md#movewindow) pour modifier la taille de la fenêtre de la feuille de propriétés.

## <a name="see-also"></a>Voir aussi

[Feuilles de propriétés](property-sheets-mfc.md)<br/>
[CPropertyPage (classe)](reference/cpropertypage-class.md)<br/>
[CPropertySheet (classe)](reference/cpropertysheet-class.md)
