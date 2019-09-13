---
title: Onglets et attributs de contrôle d'onglet
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 982ec40e330e2a7dda5c125d83e54751cd14416d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511242"
---
# <a name="tabs-and-tab-control-attributes"></a>Onglets et attributs de contrôle d'onglet

Vous bénéficiez d’un contrôle considérable sur l’apparence et le comportement des onglets qui composent un contrôle onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Chaque onglet peut avoir une étiquette, une icône, un état d’élément et une valeur 32 bits définie par l’application qui lui est associée. Pour chaque onglet, vous pouvez afficher l’icône, l’étiquette ou les deux.

En outre, chaque élément d’onglet peut avoir trois États possibles : enfoncé, non enfoncé ou mis en surbrillance. Cet État ne peut être défini qu’en modifiant un élément d’onglet existant. Pour modifier un élément d’onglet existant, récupérez-le à l’aide d’un appel à [GetItem](../mfc/reference/ctabctrl-class.md#getitem), modifiez la structure `TCITEM` (en particulier les données membres *dwState* et *dwStateMask*), puis retournez la structure modifiée `TCITEM` avec un appel à [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Si vous devez effacer l’état des éléments de tous les onglets d’un `CTabCtrl` objet, effectuez un appel à [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Cette fonction réinitialise l’état de tous les éléments d’onglet ou tous les éléments à l’exception de celui qui est actuellement sélectionné.

Le code suivant efface l’état de tous les éléments d’onglet, puis modifie l’état du troisième élément :

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Pour plus d’informations sur les attributs de tabulation, consultez onglets [et attributs de tabulation](/windows/win32/Controls/tab-controls) dans la SDK Windows. Pour plus d’informations sur l’ajout d’onglets à un contrôle onglet, consultez [Ajout d’onglets à un contrôle onglet](../mfc/adding-tabs-to-a-tab-control.md) plus loin dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
