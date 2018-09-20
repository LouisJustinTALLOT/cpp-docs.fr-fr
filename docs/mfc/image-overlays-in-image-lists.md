---
title: Image des superpositions dans les listes d’images | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- overlays [MFC]
- image lists [MFC], image overlays in
- CImageList class [MFC], image overlays in
ms.assetid: aaf4e1c4-cd12-42c8-9af4-1bb458889b4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c4052e06fe8aae1d149c3c09e88715d8270b361
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426560"
---
# <a name="image-overlays-in-image-lists"></a>Superpositions d'images dans les listes d'images

Chaque liste d’images ([CImageList](../mfc/reference/cimagelist-class.md)) inclut une liste d’images à utiliser comme masques de superposition. Un masque de « superposition » est une image dessinée en toute transparence sur une autre image. N’importe quelle image peut être utilisée comme un masque de superposition. Vous pouvez spécifier jusqu'à quatre masques de superposition par liste d’images.

Vous ajoutez l’index d’une image à la liste des masques de superposition à l’aide de la [fonction membre SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) fonction membre, l’index d’une image et l’index d’un masque de superposition. Notez que les index pour les masques de superposition sont basé sur un lieu de 0.

Vous dessinez un masque de superposition sur une image à l’aide d’un seul appel à `Draw`. Les paramètres comprennent l’index de l’image à dessiner et l’index d’un masque de superposition. Vous devez utiliser le [INDEXTOOVERLAYMASK](/windows/desktop/api/commctrl/nf-commctrl-indextooverlaymask) macro pour spécifier l’index du masque de superposition. Vous pouvez également spécifier une image de superposition lors de l’appel le [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) fonction membre.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

