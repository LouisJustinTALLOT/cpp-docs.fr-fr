---
description: 'En savoir plus sur : modification des étiquettes de contrôle d’arborescence'
title: Modification des étiquettes de contrôles d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: b471b2ce9773ec86b1e4f94e766d3428fef456fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264009"
---
# <a name="tree-control-label-editing"></a>Modification des étiquettes de contrôles d’arborescence

L’utilisateur peut modifier directement les étiquettes des éléments dans un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) qui a le style **TVS_EDITLABELS** . L’utilisateur commence la modification en cliquant sur l’étiquette de l’élément qui a le focus. Une application commence la modification à l’aide de la fonction membre [EditLabel](../mfc/reference/ctreectrl-class.md#editlabel) . Le contrôle d’arborescence envoie la notification lorsque la modification commence et lorsqu’elle est annulée ou terminée. Lorsque la modification est terminée, vous êtes responsable de la mise à jour de l’étiquette de l’élément, le cas échéant.

Lorsque la modification d’étiquette commence, un contrôle d’arborescence envoie un message de notification [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) . En traitant cette notification, vous pouvez autoriser la modification de certaines étiquettes et empêcher la modification des autres. Si la valeur 0 est retournée, la modification est retournée et une valeur différente de zéro l’empêche.

Lorsque la modification d’étiquette est annulée ou terminée, un contrôle d’arborescence envoie un message de notification [TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit) . Le paramètre *lParam* est l’adresse d’une structure [NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow) . Le membre de l' **élément** est une structure [TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw) qui identifie l’élément et qui comprend le texte modifié. Vous êtes responsable de la mise à jour de l’étiquette de l’élément, le cas échéant, éventuellement après la validation de la chaîne modifiée. Le membre *pszText* de `TV_ITEM` est 0 si la modification est annulée.

Pendant la modification des étiquettes, en général en réponse au message de notification [TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit) , vous pouvez obtenir un pointeur vers le contrôle d’édition utilisé pour la modification d’étiquette à l’aide de la fonction membre [GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol) . Vous pouvez appeler la fonction membre [SetLimitText](../mfc/reference/cedit-class.md#setlimittext) du contrôle d’édition pour limiter la quantité de texte qu’un utilisateur peut entrer ou sous-classer dans le contrôle d’édition pour intercepter et ignorer les caractères non valides. Notez, toutefois, que le contrôle d’édition s’affiche uniquement *après* l’envoi de **TVN_BEGINLABELEDIT** .

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
