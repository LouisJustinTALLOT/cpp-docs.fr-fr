---
title: Image des informations contenues dans les listes d’images | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c98bc629cde74cf7a6fc8a416de862f50a1dd5ae
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422283"
---
# <a name="image-information-in-image-lists"></a>informations relatives aux images dans les listes d'images

[CImageList](../mfc/reference/cimagelist-class.md) inclut un certain nombre de fonctions qui récupèrent des informations à partir d’une liste d’images. Le [fonction membre GetImageInfo](../mfc/reference/cimagelist-class.md#getimageinfo) fonction membre remplit une `IMAGEINFO` structure avec des informations sur une seule image, y compris les handles de l’image et le masque les bitmaps, le nombre de plans de couleur et de bits par pixel et le rectangle englobant de l’image dans la bitmap de l’image. Vous pouvez utiliser ces informations pour manipuler directement les bitmaps pour l’image.

Le [GetImageCount](../mfc/reference/cimagelist-class.md#getimagecount) fonction membre récupère le nombre d’images dans une liste d’images.

Vous pouvez créer une icône basée sur une image et un masque dans une liste d’images à l’aide de la [fonction membre ExtractIcon](../mfc/reference/cimagelist-class.md#extracticon) fonction membre. La fonction retourne le handle de la nouvelle icône.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)

