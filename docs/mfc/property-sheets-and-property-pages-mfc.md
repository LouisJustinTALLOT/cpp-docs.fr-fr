---
title: Pages et feuilles de propriétés (MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- MFC dialog boxes [MFC], tabs
- property pages [MFC], property sheets
- CPropertyPage class [MFC], property sheets and pages
- CPropertySheet class [MFC], property sheets and pages
- property sheets, propert pages
ms.assetid: de8fea12-6c35-4cef-8625-b8073a379446
ms.openlocfilehash: 5d4fd1c957b7f4d0d6ad10379a448309743aa11a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685081"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Pages et feuilles de propriétés (MFC)

Une [boîte de dialogue](../mfc/dialog-boxes.md) MFC peut s’afficher dans une boîte de dialogue d’onglets en incorporant des feuilles de propriétés et des pages de propriétés. Appelée « feuille de propriétés » dans MFC, ce type de boîte de dialogue, similaire à de nombreuses boîtes de dialogue dans Microsoft Word, Excel C++et visuel, semble contenir une pile de feuilles à onglets, comme une pile de dossiers de fichiers vus de l’avant vers l’arrière ou un groupe de fenêtres en cascade. Les contrôles de l’onglet avant sont visibles ; seul l’onglet étiqueté est visible dans les onglets arrière. Les feuilles de propriétés sont particulièrement utiles pour gérer un grand nombre de propriétés ou de paramètres qui se situent assez clairement dans plusieurs groupes. En règle générale, une feuille de propriétés peut simplifier une interface utilisateur en remplaçant plusieurs boîtes de dialogue distinctes.

À partir de la version 4,0 de MFC, les feuilles de propriétés et les pages de propriétés sont implémentées à l’aide des contrôles communs fournis avec Windows 95 et Windows NT version 3,51 et ultérieure.

Les feuilles de propriétés sont implémentées avec les classes [CPropertySheet](../mfc/reference/cpropertysheet-class.md) et [CPropertyPage](../mfc/reference/cpropertypage-class.md) (décrites dans la *référence MFC*). `CPropertySheet` définit la boîte de dialogue globale, qui peut contenir plusieurs « pages » basées sur `CPropertyPage`.

Pour plus d’informations sur la création et l’utilisation des feuilles de propriétés, consultez la rubrique [feuilles de propriétés](../mfc/property-sheets-mfc.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Utilisation des boîtes de dialogue dans MFC](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Pages et feuilles de propriétés dans MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Échange des données](../mfc/exchanging-data.md)<br/>
[Création d’une feuille de propriétés non modale](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Gestion du bouton Appliquer](../mfc/handling-the-apply-button.md)
