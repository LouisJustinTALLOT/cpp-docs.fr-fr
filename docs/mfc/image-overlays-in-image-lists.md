---
title: Superpositions d'images dans les listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
ms.openlocfilehash: dc5c28a38d3024f3d8cbd1fa8b9fe9c1c8a09f93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50603097"
---
# <a name="image-overlays-in-image-lists"></a>Superpositions d'images dans les listes d'images

Chaque liste d’images ([CImageList](../mfc/reference/cimagelist-class.md)) inclut une liste d’images à utiliser comme masques de superposition. Un masque de « superposition » est une image dessinée en toute transparence sur une autre image. N’importe quelle image peut être utilisée comme un masque de superposition. Vous pouvez spécifier jusqu'à quatre masques de superposition par liste d’images.

Vous ajoutez l’index d’une image à la liste des masques de superposition à l’aide de la [fonction membre SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) fonction membre, l’index d’une image et l’index d’un masque de superposition. Notez que les index pour les masques de superposition sont basé sur un lieu de 0.

Vous dessinez un masque de superposition sur une image à l’aide d’un seul appel à `Draw`. Les paramètres comprennent l’index de l’image à dessiner et l’index d’un masque de superposition. Vous devez utiliser le [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) macro pour spécifier l’index du masque de superposition. Vous pouvez également spécifier une image de superposition lors de l’appel le [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) fonction membre.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

