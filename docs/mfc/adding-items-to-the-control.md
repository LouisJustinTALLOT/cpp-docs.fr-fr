---
title: Ajout d'éléments au contrôle
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], adding items
ms.assetid: 715994bd-340d-4ad2-9882-411654137830
ms.openlocfilehash: 5cc1c7a921cf6d6ba2c0f968012b48bfcaef0658
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623363"
---
# <a name="adding-items-to-the-control"></a>Ajout d'éléments au contrôle

Pour ajouter des éléments au contrôle de liste ([CListCtrl](reference/clistctrl-class.md)), appelez l’une des différentes versions de la fonction membre [InsertItem](reference/clistctrl-class.md#insertitem) , en fonction des informations que vous avez. Une version prend une structure [LVITEM](/windows/win32/api/commctrl/ns-commctrl-lvitemw) que vous préparez. Étant donné que la `LVITEM` structure contient de nombreux membres, vous disposez d’un contrôle accru sur les attributs de l’élément de contrôle de liste.

Deux membres importants (en ce qui concerne la vue rapport) de la `LVITEM` structure sont `iItem` les `iSubItem` membres et. Le `iItem` membre est l’index de base zéro de l’élément auquel la structure fait référence et le `iSubItem` membre est l’index de base un d’un sous-élément, ou zéro si la structure contient des informations sur un élément. Avec ces deux membres, vous déterminez, par élément, le type et la valeur des informations de sous-élément qui s’affichent lorsque le contrôle de liste est en mode rapport. Pour plus d’informations, consultez [CListCtrl :: SetItem](reference/clistctrl-class.md#setitem).

Les membres supplémentaires spécifient le texte, l’icône, l’État et les données d’élément de l’élément. « Data Item » est une valeur définie par l’application associée à un élément d’affichage de liste. Pour plus d’informations sur la `LVITEM` structure, consultez [CListCtrl :: GetItem](reference/clistctrl-class.md#getitem).

D’autres versions de `InsertItem` acceptent une ou plusieurs valeurs distinctes, correspondant aux membres de la `LVITEM` structure, ce qui vous permet d’initialiser uniquement les membres que vous souhaitez prendre en charge. En règle générale, le contrôle de liste gère le stockage pour les éléments de liste, mais vous pouvez stocker certaines informations dans votre application à la place, à l’aide de « éléments de rappel ». Pour plus d’informations, consultez [éléments de rappel et masque de rappel](callback-items-and-the-callback-mask.md) dans cette rubrique, ainsi que [les éléments de rappel et le masque de rappel](/windows/win32/Controls/using-list-view-controls) dans la SDK Windows.

Pour plus d’informations, consultez [Ajout d’éléments de liste et de sous-éléments](/windows/win32/Controls/using-list-view-controls).

## <a name="see-also"></a>Voir aussi

[Utilisation de CListCtrl](using-clistctrl.md)<br/>
[Commandes](controls-mfc.md)
