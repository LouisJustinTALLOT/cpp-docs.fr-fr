---
title: Position d’élément de contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
ms.openlocfilehash: 238cb40319d28a53592a594a72947f400720f935
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2019
ms.locfileid: "57278377"
---
# <a name="tree-control-item-position"></a>Position d’élément de contrôle d’arborescence

Position initiale d’un élément est définie lorsque l’élément est ajouté au contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) à l’aide de la `InsertItem` fonction membre. L’appel de fonction membre spécifie le handle de l’élément parent et le handle de l’élément après lequel le nouvel élément doit être inséré. Le deuxième handle doit identifier un élément enfant du parent donné ou une de ces valeurs : `TVI_FIRST`, `TVI_LAST`, ou `TVI_SORT`.

Lorsque `TVI_FIRST` ou `TVI_LAST` est spécifié, le contrôle d’arborescence place le nouvel élément au début ou à la fin de la liste de l’élément parent donné d’éléments enfants. Lorsque `TVI_SORT` est spécifié, le contrôle d’arborescence insère le nouvel élément dans la liste des éléments enfants dans l’ordre alphabétique selon le texte des étiquettes.

Vous pouvez placer la liste d’un élément parent des éléments enfants dans l’ordre alphabétique en appelant le [fonction membre SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) fonction membre. Cette fonction inclut un paramètre qui spécifie si tous les niveaux d’éléments enfants décroissant à partir de l’élément parent donné sont également triés par ordre alphabétique.

Le [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) fonction membre vous permet de trier les éléments enfants en fonction de critères que vous définissez. Lorsque vous appelez cette fonction, vous spécifiez une fonction de rappel défini par l’application que le contrôle d’arborescence peut appeler chaque fois que l’ordre relatif de deux éléments enfants doit décider. La fonction de rappel reçoit deux valeurs définies par l’application 32 bits pour les éléments comparés et une troisième valeur 32 bits que vous spécifiez lors de l’appel `SortChildrenCB`.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
