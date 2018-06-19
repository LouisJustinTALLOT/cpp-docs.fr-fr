---
title: Image des superpositions dans les listes d’images | Documents Microsoft
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
ms.openlocfilehash: 55a55a6e015a2f8c1613a85717c030737712c4da
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33345405"
---
# <a name="image-overlays-in-image-lists"></a>Superpositions d'images dans les listes d'images
Chaque liste d’images ([CImageList](../mfc/reference/cimagelist-class.md)) inclut une liste d’images à utiliser comme masques de superposition. Un masque de « superposition » est une image dessinée en transparence sur une autre image. Toute image peut être utilisée comme un masque de superposition. Vous pouvez spécifier jusqu'à quatre masques de superposition par liste d’images.  
  
 Vous ajoutez l’index d’une image à la liste des masques de superposition à l’aide de la [fonction membre SetOverlayImage](../mfc/reference/cimagelist-class.md#setoverlayimage) fonction membre, l’index d’une image et l’index d’un masque de superposition. Notez que les indices de masques de superposition sont basés sur un au lieu de base zéro.  
  
 Vous dessinez un masque de superposition sur une image à l’aide d’un seul appel à **dessiner**. Les paramètres comprennent l’index de l’image à dessiner et l’index d’un masque de superposition. Vous devez utiliser le [INDEXTOOVERLAYMASK](http://msdn.microsoft.com/library/windows/desktop/bb761408) macro pour spécifier l’index du masque de superposition. Vous pouvez également spécifier une image de superposition lors de l’appel du [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect) fonction membre.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CImageList](../mfc/using-cimagelist.md)   
 [Contrôles](../mfc/controls-mfc.md)

