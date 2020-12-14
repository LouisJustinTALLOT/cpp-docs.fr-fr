---
description: 'En savoir plus sur : informations sur les éléments de contrôle d’arborescence'
title: Informations sur les éléments de contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- tree controls [MFC], item information
- CTreeCtrl class [MFC], item information
ms.assetid: 8dcab855-27de-49e9-95d8-f78ba963ea71
ms.openlocfilehash: ced75bdf6ed6a10e3a34536adf4af0ed1c7e0c86
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264139"
---
# <a name="tree-control-item-information"></a>Informations sur les éléments de contrôle d’arborescence

Les contrôles d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) comportent un certain nombre de fonctions membres qui récupèrent des informations sur les éléments du contrôle. La fonction membre [GetItem](../mfc/reference/ctreectrl-class.md#getitem) récupère une partie ou la totalité des données associées à un élément. Ces données peuvent inclure le texte de l’élément, l’État, les images, le nombre d’éléments enfants et une valeur de données 32 bits définie par l’application. Il existe également une fonction [SetItem](../mfc/reference/ctreectrl-class.md#setitem) qui peut définir tout ou partie des données associées à un élément.

Les fonctions membres [GetItemState](../mfc/reference/ctreectrl-class.md#getitemstate), [GetItemText](../mfc/reference/ctreectrl-class.md#getitemtext), [GetItemData](../mfc/reference/ctreectrl-class.md#getitemdata)et [GetItemImage](../mfc/reference/ctreectrl-class.md#getitemimage) récupèrent des attributs individuels d’un élément. Chacune de ces fonctions a une fonction Set correspondante pour définir les attributs d’un élément.

La fonction membre [GetNextItem](../mfc/reference/ctreectrl-class.md#getnextitem) récupère l’élément de contrôle d’arborescence qui porte la relation spécifiée à l’élément actuel. Cette fonction peut récupérer le parent d’un élément, l’élément visible suivant ou précédent, le premier élément enfant, et ainsi de suite. Il existe également des fonctions membres pour parcourir l’arborescence : [GetRootItem](../mfc/reference/ctreectrl-class.md#getrootitem), [GetFirstVisibleItem](../mfc/reference/ctreectrl-class.md#getfirstvisibleitem), [GetNextVisibleItem](../mfc/reference/ctreectrl-class.md#getnextvisibleitem), [GetPrevVisibleItem](../mfc/reference/ctreectrl-class.md#getprevvisibleitem), [GetChildItem](../mfc/reference/ctreectrl-class.md#getchilditem), [GetNextSiblingItem](../mfc/reference/ctreectrl-class.md#getnextsiblingitem), [GetPrevSiblingItem](../mfc/reference/ctreectrl-class.md#getprevsiblingitem), [GetParentItem](../mfc/reference/ctreectrl-class.md#getparentitem), [GetSelectedItem](../mfc/reference/ctreectrl-class.md#getselecteditem)et [GetDropHilightItem](../mfc/reference/ctreectrl-class.md#getdrophilightitem).

La fonction membre [GetItemRect](../mfc/reference/ctreectrl-class.md#getitemrect) récupère le rectangle englobant d’un élément de contrôle d’arborescence. Les fonctions membres [GetCount](../mfc/reference/ctreectrl-class.md#getcount) et [GetVisibleCount](../mfc/reference/ctreectrl-class.md#getvisiblecount) récupèrent le nombre d’éléments dans un contrôle d’arborescence et le nombre d’éléments qui sont actuellement visibles dans la fenêtre du contrôle d’arborescence, respectivement. Vous pouvez vous assurer qu’un élément particulier est visible en appelant la fonction membre [EnsureVisible](../mfc/reference/ctreectrl-class.md#ensurevisible) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
