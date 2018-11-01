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
ms.openlocfilehash: ba63fdca32af28d0763dd4cf2da3465a99ddeb1f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571988"
---
# <a name="tabs-and-tab-control-attributes"></a>Onglets et attributs de contrôle d'onglet

Vous avez un contrôle important sur l’apparence et le comportement des onglets qui composent un contrôle onglet ([CTabCtrl](../mfc/reference/ctabctrl-class.md)). Chaque onglet peut avoir une étiquette, une icône, un état d’élément et une valeur 32 bits définie par l’application associée. Pour chaque onglet, vous pouvez afficher l’icône, l’étiquette ou les deux.

En outre, chaque élément d’onglet peut avoir trois états possibles : enfoncé, non pressé ou mis en surbrillance. Cet état peut uniquement être défini en modifiant un élément d’onglet existant. Pour modifier un élément d’onglet existant, récupérer avec un appel à [GetItem](../mfc/reference/ctabctrl-class.md#getitem), modifiez le `TCITEM` structure (en particulier le *dwState* et *dwStateMask* membres de données ), puis revenez modifié `TCITEM` structure avec un appel à [SetItem](../mfc/reference/ctabctrl-class.md#setitem). Si vous devez effacer les États des éléments de tous les éléments d’onglet dans un `CTabCtrl` d’objet, effectuez un appel à [DeselectAll](../mfc/reference/ctabctrl-class.md#deselectall). Cette fonction réinitialise l’état de tous les éléments d’onglet ou tous les éléments à l’exception de celui actuellement sélectionné.

Le code suivant efface l’état de tous les éléments d’onglet, puis modifie l’état de la troisième élément :

[!code-cpp[NVC_MFCControlLadenDialog#32](../mfc/codesnippet/cpp/tabs-and-tab-control-attributes_1.cpp)]

Pour plus d’informations sur les attributs de l’onglet, consultez [onglets et attributs de l’onglet](/windows/desktop/Controls/tab-controls) dans le SDK Windows. Pour plus d’informations sur l’ajout d’onglets à un contrôle onglet, consultez [Ajout d’onglets à un contrôle Tab](../mfc/adding-tabs-to-a-tab-control.md) plus loin dans cette rubrique.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

