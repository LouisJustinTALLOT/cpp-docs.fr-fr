---
title: Superpositions d'images dans les listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: ec795193a28a68d8aee61e9932481a89c4b3e8e0
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508390"
---
# <a name="image-overlays-in-image-lists"></a>Superpositions d'images dans les listes d'images

Chaque liste d’images ([CImageList](../mfc/reference/cimagelist-class.md)) comprend une liste d’images à utiliser comme masques de superposition. Un «masque de superposition» est une image dessinée de façon transparente sur une autre image. Une image peut être utilisée comme masque de superposition. Vous pouvez spécifier jusqu’à quatre masques de superposition par liste d’images.

Vous ajoutez l’index d’une image à la liste des masques de recouvrement à l’aide de la fonction membre [SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) , de l’index d’une image et de l’index d’un masque de superposition. Notez que les index des masques de superposition sont basés sur un et non sur zéro.

Vous dessinez un masque de superposition sur une image à l' `Draw`aide d’un seul appel à. Les paramètres incluent l’index de l’image à dessiner et l’index d’un masque de superposition. Vous devez utiliser la macro [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask) pour spécifier l’index du masque de superposition. Vous pouvez également spécifier une image de superposition lors de l’appel de la fonction membre [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) .

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
