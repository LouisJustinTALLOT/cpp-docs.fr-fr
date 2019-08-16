---
title: Faire glisser des images à partir d'une liste d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
ms.openlocfilehash: 3035e6f21d38568b364fce02358c3baed4870bc3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508650"
---
# <a name="dragging-images-from-an-image-list"></a>Faire glisser des images à partir d'une liste d'images

[CImageList](../mfc/reference/cimagelist-class.md) comprend des fonctions permettant de faire glisser une image à l’écran. Les fonctions Glisser-déplacer déplacent une image en douceur, en couleurs, sans aucun clignotement du curseur. Les images masquées et démasquées peuvent être glissées.

La fonction membre [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) commence une opération glisser. Les paramètres incluent l'index de l'image à faire glisser et l'emplacement de la zone réactive dans l'image. La zone réactive est un seul pixel que les fonctions de glissement identifient comme l'emplacement exact de l'image à l'écran. Généralement, une application définit la zone réactive afin qu'elle coïncide avec la zone réactive du curseur de la souris. La fonction membre [DragMove](../mfc/reference/cimagelist-class.md#dragmove) déplace l’image vers un nouvel emplacement.

La fonction membre [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) définit la position initiale de l’image de glissement dans une fenêtre et dessine l’image à la position. Les paramètres incluent un pointeur vers la fenêtre dans laquelle ajouter l'image et un point qui spécifie les détails de la position initiale dans la fenêtre. Les coordonnées sont exprimées par rapport au coin supérieur gauche de la fenêtre, pas de la zone cliente. Il en va de même pour toutes les fonctions de glissement d'image qui prennent des coordonnées en tant que paramètres. Cela signifie que vous devez compenser la largeur des éléments de la fenêtre, telles que la bordure, la barre de titre et la barre de menus, lors de la spécification des coordonnées. Si vous spécifiez un handle de fenêtre null `DragEnter`lors de l’appel de, les fonctions de glissement dessinent l’image dans le contexte de périphérique associé à la fenêtre du bureau, et les coordonnées sont relatives au coin supérieur gauche de l’écran.

`DragEnter` verrouille toutes les mises à jour dans la fenêtre donnée pendant l'opération de glissement. Si vous devez effectuer un dessin au cours d’une opération glisser, telle que la mise en surbrillance de la cible d’une opération de glisser-déplacer, vous pouvez masquer temporairement l’image glissée à l’aide de la fonction membre [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) . Vous pouvez également utiliser la fonction membre [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) .

Appelez [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) lorsque vous avez terminé de faire glisser l’image.

La fonction membre [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) crée une image de glissement en combinant l’image donnée (généralement une image de curseur de la souris) avec l’image de glissement actuelle. Étant donné que les fonctions de glissement utilisent la nouvelle image pendant une opération de glissement, vous devez utiliser la fonction [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) de Windows pour masquer `SetDragCursorImage`le curseur de la souris réel après l’appel de. Sinon, le système peut sembler être composé de deux curseurs de souris pour la durée de l'opération Glisser-déplacer.

Lorsqu'une application appelle `BeginDrag`, le système crée une liste d'images temporaire interne et copie l'image glissée spécifiée dans la liste interne. Vous pouvez récupérer un pointeur vers la liste d’images de glissement temporaire à l’aide de la fonction membre [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) . La fonction récupère également l'emplacement actuel de glissement et le décalage de l'image glissée par rapport à la position de glissement.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
