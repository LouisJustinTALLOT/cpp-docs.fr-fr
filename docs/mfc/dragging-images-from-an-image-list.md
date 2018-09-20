---
title: Faire glisser des Images à partir d’une liste d’images | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], dragging images from
- dragging images from image lists [MFC]
- image lists [MFC], dragging images from
- images [MFC], dragging from image lists
ms.assetid: af691db8-e4f0-4046-b7b9-9acc68d3713d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fb872cba298d6d18ab5287a285b22d2f568fa04b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46382373"
---
# <a name="dragging-images-from-an-image-list"></a>Faire glisser des images à partir d'une liste d'images

[CImageList](../mfc/reference/cimagelist-class.md) inclut des fonctions permettant de faire glisser une image sur l’écran. Les fonctions Glisser-déplacer déplacent une image en douceur, en couleurs, sans aucun clignotement du curseur. Les images masquées et démasquées peuvent être glissées.

Le [BeginDrag](../mfc/reference/cimagelist-class.md#begindrag) fonction membre commence une opération glisser. Les paramètres incluent l'index de l'image à faire glisser et l'emplacement de la zone réactive dans l'image. La zone réactive est un seul pixel que les fonctions de glissement identifient comme l'emplacement exact de l'image à l'écran. Généralement, une application définit la zone réactive afin qu'elle coïncide avec la zone réactive du curseur de la souris. Le [DragMove](../mfc/reference/cimagelist-class.md#dragmove) fonction membre déplace l’image vers un nouvel emplacement.

Le [DragEnter](../mfc/reference/cimagelist-class.md#dragenter) fonction membre définit la position initiale de l’image glissée dans une fenêtre et dessine l’image à la position. Les paramètres incluent un pointeur vers la fenêtre dans laquelle ajouter l'image et un point qui spécifie les détails de la position initiale dans la fenêtre. Les coordonnées sont exprimées par rapport au coin supérieur gauche de la fenêtre, pas de la zone cliente. Il en va de même pour toutes les fonctions de glissement d'image qui prennent des coordonnées en tant que paramètres. Cela signifie que vous devez compenser la largeur des éléments de la fenêtre, telles que la bordure, la barre de titre et la barre de menus, lors de la spécification des coordonnées. Si vous spécifiez un **NULL** handle de fenêtre lors de l’appel `DragEnter`, les fonctions de glissement dessinent l’image dans le contexte de périphérique associé à la fenêtre du bureau et les coordonnées sont exprimées par rapport à l’angle supérieur gauche de l’écran.

`DragEnter` verrouille toutes les mises à jour dans la fenêtre donnée pendant l'opération de glissement. Si vous avez besoin effectuer un dessin pendant une opération glisser, telles que la mise en surbrillance de la cible d’une opération de glisser-déplacer, vous pouvez masquer temporairement l’image à l’aide de la [DragLeave](../mfc/reference/cimagelist-class.md#dragleave) fonction membre. Vous pouvez également utiliser le [DragShowNoLock](../mfc/reference/cimagelist-class.md#dragshownolock) fonction membre.

Appelez [EndDrag](../mfc/reference/cimagelist-class.md#enddrag) lorsque vous avez terminé en faisant glisser l’image.

Le [SetDragCursorImage](../mfc/reference/cimagelist-class.md#setdragcursorimage) fonction membre crée une nouvelle image glisser en combinant l’image donnée (généralement une image de curseur de souris) avec l’image glissée actuelle. Étant donné que les fonctions de glissement utilisent la nouvelle image pendant une opération glisser, vous devez utiliser le Windows [ShowCursor](/windows/desktop/api/winuser/nf-winuser-showcursor) (fonction) pour masquer le curseur de souris réel après avoir appelé `SetDragCursorImage`. Sinon, le système peut sembler être composé de deux curseurs de souris pour la durée de l'opération Glisser-déplacer.

Lorsqu'une application appelle `BeginDrag`, le système crée une liste d'images temporaire interne et copie l'image glissée spécifiée dans la liste interne. Vous pouvez récupérer un pointeur vers la liste d’images à l’aide de la [GetDragImage](../mfc/reference/cimagelist-class.md#getdragimage) fonction membre. La fonction récupère également l'emplacement actuel de glissement et le décalage de l'image glissée par rapport à la position de glissement.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

