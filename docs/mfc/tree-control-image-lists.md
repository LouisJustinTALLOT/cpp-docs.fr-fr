---
description: 'En savoir plus sur : listes d’images de contrôle d’arborescence'
title: Listes d'images de contrôle d'arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: ce76cca5642208d4158b36c45c150202270258e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97264152"
---
# <a name="tree-control-image-lists"></a>Listes d'images de contrôle d'arborescence

Chaque élément d’un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) peut avoir une paire d’images bitmap qui lui sont associées. Les images apparaissent à gauche de l'étiquette d'un élément. Une image est affichée lorsque l'élément est sélectionné, et l'autre est affichée lorsque l'élément n'est pas sélectionné. Par exemple, un élément peut afficher un dossier ouvert lorsqu’il est sélectionné et un dossier fermé lorsqu’il ne l’est pas.

Pour utiliser des images d’élément, vous devez créer une liste d’images en construisant un objet [CImageList](../mfc/reference/cimagelist-class.md) et en utilisant la fonction [CImageList :: Create](../mfc/reference/cimagelist-class.md#create) pour créer la liste d’images associée. Ajoutez ensuite les bitmaps souhaitées à la liste et associez la liste au contrôle d’arborescence à l’aide de la fonction membre [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) . Par défaut, tous les éléments affichent la première image de la liste d'images pour les états sélectionnés et non sélectionnés. Vous pouvez modifier le comportement par défaut d’un élément particulier en spécifiant les index des images sélectionnées et non sélectionnées lors de l’ajout de l’élément au contrôle d’arborescence à l’aide de la fonction membre [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) . Vous pouvez modifier les index après l’ajout d’un élément à l’aide de la fonction membre [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) .

Les listes d’images d’un contrôle d’arborescence peuvent également contenir des images de superposition, qui sont conçues pour être superposées sur des images d’élément. Une valeur autre que zéro en bits 8 à 11 de l'état d'un élément de contrôle d'arborescence spécifie l'index de base un d'une image de superposition (0 indique aucune image de superposition). Comme un index de base un de 4 bits est utilisé, les images de superposition doivent figurer parmi les 15 premières images des listes d'images. Pour plus d’informations sur les États des éléments de contrôle d’arborescence, consultez [vue d’ensemble des États des éléments de contrôle d’arborescence](../mfc/tree-control-item-states-overview.md) plus haut dans cette rubrique.

Si une liste d’images d’état est spécifiée, un contrôle d’arborescence réserve un espace à gauche de l’icône de chaque élément pour une image d’état. Une application peut utiliser des images d'état, telles que des cases à cocher activées et désactivées, pour indiquer des états d'élément définis par l'application. Une valeur autre que zéro en bits 12 à 15 spécifie l'index de base un d'une image d'état (0 indique aucune image d'état).

En spécifiant la valeur **I_IMAGECALLBACK** au lieu de l’index d’une image, vous pouvez différer la spécification de l’image sélectionnée ou non sélectionnée jusqu’à ce que l’élément soit sur le point d’être redessiné. **I_IMAGECALLBACK** indique au contrôle d’arborescence d’interroger l’application pour l’index en envoyant le message de notification [TVN_GETDISPINFO](/windows/win32/Controls/tvn-getdispinfo) .

La fonction membre [GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) récupère le handle de la liste d’images d’un contrôle d’arborescence. Cette fonction est utile si vous devez ajouter d'autres images à la liste. Pour plus d’informations sur les listes d’images, consultez [utilisation de CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) dans la *référence MFC* et [listes d’images](/windows/win32/controls/image-lists) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
