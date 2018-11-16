---
title: Listes d’images de contrôle d’arborescence
ms.date: 11/04/2016
helpviewer_keywords:
- images [MFC], lists in tree controls
- tree controls [MFC], image lists
- CTreeCtrl class [MFC], image lists
ms.assetid: f560c4f2-20d2-4d28-ac33-4017e65fb0a6
ms.openlocfilehash: e42e601fbf803f8ccfe359a10664149ac8f11086
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693243"
---
# <a name="tree-control-image-lists"></a>Listes d’images de contrôle d’arborescence

Chaque élément dans un contrôle d’arborescence ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) peut avoir une paire d’images bitmap, il est associé. Les images apparaissent à gauche de l'étiquette d'un élément. Une image est affichée lorsque l'élément est sélectionné, et l'autre est affichée lorsque l'élément n'est pas sélectionné. Par exemple, un élément peut afficher un dossier ouvert lorsqu’il est sélectionné et un dossier fermé lorsqu’il ne l’est pas.

Pour utiliser des images d’élément, vous devez créer une liste d’images en construisant un [CImageList](../mfc/reference/cimagelist-class.md) objet et à l’aide de la [CImageList::Create](../mfc/reference/cimagelist-class.md#create) fonction permettant de créer la liste d’images associée. Ajouter les bitmaps de votre choix à la liste, puis associer la liste avec le contrôle d’arborescence à l’aide de la [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist) fonction membre. Par défaut, tous les éléments affichent la première image de la liste d'images pour les états sélectionnés et non sélectionnés. Vous pouvez modifier le comportement par défaut pour un élément particulier en spécifiant les index des images sélectionnés et lors de l’ajout de l’élément au contrôle arborescence en utilisant la [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) fonction membre. Vous pouvez modifier les index après avoir ajouté un élément à l’aide de la [SetItemImage](../mfc/reference/ctreectrl-class.md#setitemimage) fonction membre.

Les listes d’images d’un contrôle d’arborescence peuvent également contenir des images de superposition, qui sont conçues pour être superposées sur des images d’élément. Une valeur autre que zéro en bits 8 à 11 de l'état d'un élément de contrôle d'arborescence spécifie l'index de base un d'une image de superposition (0 indique aucune image de superposition). Comme un index de base un de 4 bits est utilisé, les images de superposition doivent figurer parmi les 15 premières images des listes d'images. Pour plus d’informations sur les États de contrôle d’élément d’arborescence, consultez [vue d’ensemble des États éléments contrôle arborescence](../mfc/tree-control-item-states-overview.md) plus haut dans cette rubrique.

Si une liste d’images d’état est spécifiée, un contrôle d’arborescence réserve un espace à gauche de l’icône de chaque élément pour une image d’état. Une application peut utiliser des images d'état, telles que des cases à cocher activées et désactivées, pour indiquer des états d'élément définis par l'application. Une valeur autre que zéro en bits 12 à 15 spécifie l'index de base un d'une image d'état (0 indique aucune image d'état).

En spécifiant le **I_IMAGECALLBACK** valeur au lieu de l’index d’une image, vous pouvez différer la spécification de l’image sélectionnée ou non sélectionnée jusqu'à ce que l’élément est sur le point d’être redessiné. **I_IMAGECALLBACK** dirige le contrôle d’arborescence pour interroger l’application pour l’index en envoyant le [TVN_GETDISPINFO](/windows/desktop/Controls/tvn-getdispinfo) message de notification.

Le [GetImageList](../mfc/reference/ctreectrl-class.md#getimagelist) fonction membre récupère le handle de la liste d’images d’un contrôle d’arborescence. Cette fonction est utile si vous devez ajouter d'autres images à la liste. Pour plus d’informations sur les listes d’images, consultez [utilisation de CImageList](../mfc/using-cimagelist.md), [CImageList](../mfc/reference/cimagelist-class.md) dans le *référence MFC*, et [listes d’images](/windows/desktop/controls/image-lists) dans le Windows SDK.

## <a name="see-also"></a>Voir aussi

[Utilisation de CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

