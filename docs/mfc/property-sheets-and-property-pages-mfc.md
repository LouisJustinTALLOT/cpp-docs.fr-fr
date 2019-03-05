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
ms.openlocfilehash: 7ff2851cc4ed04a64f1a49d68b6e3143b5edccd8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278758"
---
# <a name="property-sheets-and-property-pages-mfc"></a>Pages et feuilles de propriétés (MFC)

Une MFC [boîte de dialogue](../mfc/dialog-boxes.md) peuvent effectuer sur un coup de œil « onglet de boîte de dialogue » en incorporant des feuilles de propriétés et pages de propriétés. Appelé une « feuille de propriétés » dans MFC, ce type de boîte de dialogue similaire à nombreuses boîtes de dialogue dans Microsoft Word, Excel et Visual C++, semble contenir une pile de feuilles à onglets, comme une pile de dossiers de fichiers vu avant en arrière, ou un groupe de fenêtres en cascade. Contrôles sous l’onglet serveur frontal sont visibles ; seul l’onglet étiqueté est visible sur les onglets. Feuilles de propriétés sont particulièrement utiles pour la gestion de grands nombres de propriétés ou paramètres répartis assez nettement en plusieurs groupes. En règle générale, une feuille de propriétés peut simplifier une interface utilisateur en remplaçant plusieurs boîtes de dialogue distinctes.

Depuis la version 4.0 de MFC, les feuilles de propriétés et pages de propriétés sont implémentées à l’aide de contrôles communs sont fournis avec Windows 95 et Windows NT version 3.51 et ultérieure.

Feuilles de propriétés sont implémentées avec les classes [CPropertySheet](../mfc/reference/cpropertysheet-class.md) et [CPropertyPage](../mfc/reference/cpropertypage-class.md) (décrit dans la *référence MFC*). `CPropertySheet` définit la boîte de dialogue globale, qui peut contenir plusieurs « pages » selon `CPropertyPage`.

Pour plus d’informations sur la création et utilisation des feuilles de propriétés, consultez la rubrique [feuilles de propriétés](../mfc/property-sheets-mfc.md).

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Cycle de vie d’une boîte de dialogue](../mfc/life-cycle-of-a-dialog-box.md)<br/>
[Pages et feuilles de propriétés dans MFC](../mfc/property-sheets-and-property-pages-in-mfc.md)<br/>
[Échange des données](../mfc/exchanging-data.md)<br/>
[Création d’une feuille de propriétés non modale](../mfc/creating-a-modeless-property-sheet.md)<br/>
[Gestion du bouton Appliquer](../mfc/handling-the-apply-button.md)
