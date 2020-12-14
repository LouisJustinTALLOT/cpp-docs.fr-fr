---
description: 'En savoir plus sur : position des éléments de contrôle d’arborescence'
title: Position d’élément de contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- CTreeCtrl class [MFC], item position
- item position in tree controls
- tree controls [MFC], item position
- position, CTreeCtrl items
ms.assetid: cd264344-2cf9-4d90-9ea8-c6900b6f60e7
ms.openlocfilehash: 7eeab82c48344f7e16a31b8d6962007024277dfc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264067"
---
# <a name="tree-control-item-position"></a>Position d’élément de contrôle d’arborescence

La position initiale d’un élément est définie lors de l’ajout de l’élément au contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) à l’aide de la `InsertItem` fonction membre. L’appel de fonction membre spécifie le handle de l’élément parent et le handle de l’élément après lequel le nouvel élément doit être inséré. Le deuxième descripteur doit identifier un élément enfant du parent donné ou l’une des valeurs suivantes : `TVI_FIRST` , `TVI_LAST` ou `TVI_SORT` .

Lorsque `TVI_FIRST` ou `TVI_LAST` est spécifié, le contrôle d’arborescence place le nouvel élément au début ou à la fin de la liste d’éléments enfants de l’élément parent donné. Lorsque `TVI_SORT` est spécifié, le contrôle d’arborescence insère le nouvel élément dans la liste d’éléments enfants dans l’ordre alphabétique en fonction du texte des étiquettes d’élément.

Vous pouvez placer la liste des éléments enfants d’un élément parent dans l’ordre alphabétique en appelant la fonction membre [SortChildren](../mfc/reference/ctreectrl-class.md#sortchildren) . Cette fonction comprend un paramètre qui spécifie si tous les niveaux d’éléments enfants décroissant de l’élément parent donné sont également triés par ordre alphabétique.

La fonction membre [SortChildrenCB](../mfc/reference/ctreectrl-class.md#sortchildrencb) vous permet de trier des éléments enfants en fonction de critères que vous définissez. Quand vous appelez cette fonction, vous spécifiez une fonction de rappel définie par l’application que le contrôle d’arborescence peut appeler chaque fois que l’ordre relatif de deux éléments enfants doit être déterminé. La fonction de rappel reçoit des valeurs définies par l’application 2 32 bits pour les éléments comparés et une troisième valeur 32 bits que vous spécifiez lors de l’appel à `SortChildrenCB` .

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
