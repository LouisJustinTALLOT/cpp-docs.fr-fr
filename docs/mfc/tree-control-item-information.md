---
title: Informations sur les éléments de contrôle d’arborescence | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 724e9d7c4e0ee7db80f024c30e363612cb40fed1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33385363"
---
# <a name="tree-control-item-information"></a>Informations sur les éléments de contrôle d’arborescence
Contrôles d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) contenant un nombre de fonctions membres qui récupèrent des informations sur les éléments dans le contrôle. Le [GetItem](../mfc/reference/ctreectrl-class.md#getitem) fonction membre extrait tout ou partie des données associées à un élément. Ces données peut inclure de texte de l’élément, état, images, le nombre d’éléments enfants et une valeur de données de 32 bits définies par l’application. Il existe également un [SetItem](../mfc/reference/ctreectrl-class.md#setitem) fonction que vous pouvez définir tout ou partie des données associées à un élément.  
  
 Le [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext), [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata), et [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) fonctions membres récupèrent tous les attributs d’un élément. Chacune de ces fonctions a une fonction Set correspondante pour définir les attributs d’un élément.  
  
 Le [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) fonction membre récupère l’élément de contrôle d’arborescence qui présente la relation spécifiée à l’élément actuel. Cette fonction peut extraire parent d’un élément, l’élément visible suivant ou précédent, le premier élément enfant et ainsi de suite. Il existe également des fonctions de membre pour parcourir l’arborescence : [GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem), et [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).  
  
 Le [fonction membre GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) fonction membre récupère le rectangle englobant d’un élément de l’arborescence. Le [GetCount](../mfc/reference/ctreectrl-class.md#getcount) et [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) fonctions membres récupèrent un nombre d’éléments dans un contrôle d’arborescence et le nombre des éléments qui sont actuellement visibles dans la fenêtre du contrôle de l’arborescence, respectivement. Vous pouvez vous assurer qu’un élément particulier est visible en appelant le [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Contrôles](../mfc/controls-mfc.md)

