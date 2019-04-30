---
title: Modification des étiquettes de contrôles d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 446db94ec49859e2213f00d205df57e332c85af2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62388148"
---
# <a name="tree-control-label-editing"></a>Modification des étiquettes de contrôles d’arborescence

L’utilisateur peut modifier directement les étiquettes des éléments dans un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) qui a le **TVS_EDITLABELS** style. L’utilisateur commence à modifier en cliquant sur l’étiquette de l’élément qui a le focus. Une application commence à modifier à l’aide de la [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) fonction membre. Le contrôle d’arborescence envoie la notification lors de la modification commence et lorsqu’elle est annulée ou terminée. Lorsque la modification est effectuée, vous êtes responsable de l’étiquette de l’élément de la mise à jour si nécessaire.

Quand une modification d’étiquette commence, un contrôle d’arborescence envoie un [TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit) message de notification. En traitant cette notification, vous pouvez autoriser la modification de certaines étiquettes et empêcher la modification des autres. Méthode retournant 0 autorise la modification, et l’autre valeur empêche.

Lors de la modification d’étiquette est annulée ou terminée, un contrôle d’arborescence envoie un [TVN_ENDLABELEDIT](/windows/desktop/Controls/tvn-endlabeledit) message de notification. Le *lParam* paramètre est l’adresse d’un [structure NMTVDISPINFO](/windows/desktop/api/commctrl/ns-commctrl-tagtvdispinfoa) structure. Le **élément** membre est un [structure TVITEM](/windows/desktop/api/commctrl/ns-commctrl-tagtvitema) structure qui identifie l’élément et inclut le texte modifié. Vous êtes responsable de la mise à jour étiquette de l’élément, le cas échéant, peut-être après avoir validé la chaîne modifiée. Le *pszText* membre `TV_ITEM` est 0 si la modification est annulée.

Au cours de la modification d’étiquette, généralement en réponse à la [TVN_BEGINLABELEDIT](/windows/desktop/Controls/tvn-beginlabeledit) message de notification, vous pouvez obtenir un pointeur vers le contrôle d’édition utilisé pour la modification d’étiquette à l’aide de la [fonction membre GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) membre fonction. Vous pouvez appeler le contrôle d’édition [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) fonction membre pour limiter la quantité de texte, un utilisateur peut entrer ou sous-classe le contrôle d’édition à intercepter et ignorer les caractères non valides. Notez, cependant, que le contrôle d’édition est uniquement affiché *après* **TVN_BEGINLABELEDIT** est envoyé.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
