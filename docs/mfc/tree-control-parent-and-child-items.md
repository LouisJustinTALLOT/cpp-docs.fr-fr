---
description: 'En savoir plus sur : éléments parents et enfants du contrôle d’arborescence'
title: Éléments parents et enfants du contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
ms.openlocfilehash: b1af78bf8a22c46b45e1fd8952944249c41bd5e0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263957"
---
# <a name="tree-control-parent-and-child-items"></a>Éléments parents et enfants du contrôle d'arborescence

Tout élément d’un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) peut avoir une liste de sous-éléments, appelés éléments enfants, qui lui sont associés. Un élément qui a un ou plusieurs éléments enfants est appelé un élément parent. Un élément enfant s'affiche sous l'élément parent et est mis en retrait pour l'identifier comme subordonné au parent. Un élément qui n'a aucun parent est en haut de la hiérarchie et est appelé un élément racine.

À tout moment, l‘état d‘une liste d‘éléments parents pour des éléments enfants peut être développé ou réduit. Lorsque l’état est développé, les éléments enfants apparaissent sous l’élément parent. Lorsqu'il est réduit, les éléments enfants ne sont pas affichés. La liste bascule automatiquement entre les États développés et réduits lorsque l’utilisateur double-clique sur l’élément parent ou, si le parent a le style **TVS_HASBUTTONS** , lorsque l’utilisateur clique sur le bouton associé à l’élément parent. Une application peut développer ou réduire les éléments enfants à l’aide de la fonction membre [expand](../mfc/reference/ctreectrl-class.md#expand) .

Vous ajoutez un élément à un contrôle d’arborescence en appelant la fonction membre [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) . Cette fonction retourne un handle du type **HTREEITEM** , qui identifie de façon unique l’élément. En ajoutant un élément, vous devez spécifier le descripteur de l'élément parent du nouvel élément. Si vous spécifiez **null** ou la valeur **TVI_ROOT** au lieu d’un handle d’élément parent dans la structure [TVINSERTSTRUCT](/windows/win32/api/commctrl/ns-commctrl-tvinsertstructw) ou le paramètre *hParent* , l’élément est ajouté en tant qu’élément racine.

Un contrôle d’arborescence envoie un message de notification [TVN_ITEMEXPANDING](/windows/win32/Controls/tvn-itemexpanding) lorsque la liste des éléments enfants d’un élément parent est sur le point d’être développée ou réduite. La notification vous permet d'empêcher la modification ou la définition de tous les attributs de l'élément parent qui dépendent de l'état de la liste des éléments enfants. Après avoir modifié l’état de la liste, le contrôle d’arborescence envoie un message de notification [TVN_ITEMEXPANDED](/windows/win32/Controls/tvn-itemexpanded) .

Lorsqu’une liste d’éléments enfants est développée, elle est mise en retrait par rapport à l’élément parent. Vous pouvez définir la quantité de mise en retrait à l’aide de la fonction membre [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) ou récupérer la valeur actuelle à l’aide de la fonction membre [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
