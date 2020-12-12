---
description: 'En savoir plus sur : onglets et attributs de contrôle d’onglet'
title: Onglets et attributs de contrôle d'onglet
ms.date: 11/04/2016
helpviewer_keywords:
- attributes [MFC], reference topics
- tab controls [MFC], attributes
- tabs [MFC]
- tabs [MFC], attributes
- CTabCtrl class [MFC], tab control attributes
ms.assetid: ecf190cb-f323-4751-bfdb-766dbe6bb553
ms.openlocfilehash: 9b79e2ae6558d812fa96d0b62c07eb1c41176ee5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97216351"
---
# <a name="tabs-and-tab-control-attributes"></a>Onglets et attributs de contrôle d'onglet

Vous bénéficiez d’un contrôle considérable sur l’apparence et le comportement des onglets qui composent un contrôle onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Chaque onglet peut avoir une étiquette, une icône, un état d’élément et une valeur 32 bits définie par l’application qui lui est associée. Pour chaque onglet, vous pouvez afficher l’icône, l’étiquette ou les deux.

En outre, chaque élément d’onglet peut avoir trois États possibles : enfoncé, non enfoncé ou mis en surbrillance. Cet État ne peut être défini qu’en modifiant un élément d’onglet existant. Pour modifier un élément d’onglet existant, récupérez-le à l’aide d’un appel à [GetItem](../mfc/reference/ctabctrl-class.md#getitem), modifiez la `TCITEM` structure (en particulier les données membres *dwState* et *dwStateMask* ), puis retournez la `TCITEM` structure modifiée à l’aide d’un appel à [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Si vous devez effacer l’état des éléments de tous les onglets d’un `CTabCtrl` objet, effectuez un appel à [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Cette fonction réinitialise l’état de tous les éléments d’onglet ou tous les éléments à l’exception de celui qui est actuellement sélectionné.

Le code suivant efface l’état de tous les éléments d’onglet, puis modifie l’état du troisième élément :

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Pour plus d’informations sur les attributs de tabulation, consultez onglets [et attributs de tabulation](/windows/win32/Controls/tab-controls) dans la SDK Windows. Pour plus d’informations sur l’ajout d’onglets à un contrôle onglet, consultez [Ajout d’onglets à un contrôle onglet](../mfc/adding-tabs-to-a-tab-control.md) plus loin dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
