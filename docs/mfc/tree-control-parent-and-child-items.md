---
title: Arborescence Parent du contrôle et les éléments enfants | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- parent items in CTreeCtrl [MFC]
- child items in tree control [MFC]
- CTreeCtrl class [MFC], parent and child items
- tree controls [MFC], parent and child items
ms.assetid: abcea1e4-fe9b-40d9-86dc-1db235f8f103
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7937ef604d14c464141c6e432a4d20a9d06e172
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36954505"
---
# <a name="tree-control-parent-and-child-items"></a>Éléments parents et enfants du contrôle d’arborescence
N’importe quel élément dans un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) peut comporter une liste de sous-éléments, qui sont appelés éléments enfants, il est associés. Un élément qui a un ou plusieurs éléments enfants est appelé un élément parent. Un élément enfant s'affiche sous l'élément parent et est mis en retrait pour l'identifier comme subordonné au parent. Un élément qui n'a aucun parent est en haut de la hiérarchie et est appelé un élément racine.  
  
 À tout moment, l'état d'une liste d'éléments parents pour des éléments enfants peut être développé ou réduit. Lorsque l'état est développé, les éléments enfants apparaissent sous l'élément parent. Lorsqu‘il est réduit, les éléments enfants ne sont pas affichés. La liste bascule automatiquement entre les États développés ou réduits lorsque l’utilisateur double-clique sur l’élément parent ou, si le parent a le **TVS_HASBUTTONS** style, lorsque l’utilisateur clique sur le bouton associé à l’élément parent. Une application peut augmenter ou réduire les éléments enfants à l’aide de la [Expand](../mfc/reference/ctreectrl-class.md#expand) fonction membre.  
  
 Vous ajoutez un élément à un contrôle d’arborescence en appelant le [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) fonction membre. Cette fonction retourne un handle de la **HTREEITEM** type, qui identifie de façon unique l’élément. En ajoutant un élément, vous devez spécifier le descripteur de l'élément parent du nouvel élément. Si vous spécifiez **NULL** ou **TVI_ROOT** valeur au lieu d’un handle d’élément parent dans le [TVINSERTSTRUCT](http://msdn.microsoft.com/library/windows/desktop/bb773452) structure ou *hParent* paramètre, l’élément est ajouté en tant qu’un élément racine.  
  
 Un contrôle d’arborescence envoie un [TVN_ITEMEXPANDING](http://msdn.microsoft.com/library/windows/desktop/bb773537) message de notification lors de la liste d’un élément parent des éléments enfants est sur le point d’être développée ou réduite. La notification vous permet d’empêcher la modification ou la définition de tous les attributs de l’élément parent qui dépendent de l’état de la liste des éléments enfants. Après avoir modifié l’état de la liste, le contrôle d’arborescence envoie un [TVN_ITEMEXPANDED](http://msdn.microsoft.com/library/windows/desktop/bb773533) message de notification.  
  
 Lorsqu’une liste d’éléments enfants est développée, elle est mise en retrait par rapport à l’élément parent. Vous pouvez définir la quantité de mise en retrait à l’aide de la [SetIndent](../mfc/reference/ctreectrl-class.md#setindent) fonction membre ou récupérer la valeur actuelle à l’aide de la [GetIndent](../mfc/reference/ctreectrl-class.md#getindent) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

