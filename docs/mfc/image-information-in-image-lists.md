---
description: 'En savoir plus sur : informations sur l’image dans les listes d’images'
title: informations relatives aux images dans les listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], image information in
- image lists [MFC], image information in
ms.assetid: 73c41543-fa91-405d-b15b-0feffa6a72c1
ms.openlocfilehash: c3a5f1cee0a06177d12b72673bf0ebf8e1a73933
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97290139"
---
# <a name="image-information-in-image-lists"></a>informations relatives aux images dans les listes d'images

[CImageList](reference/cimagelist-class.md) comprend un certain nombre de fonctions qui récupèrent des informations à partir d’une liste d’images. La fonction membre [GetImageInfo](reference/cimagelist-class.md#getimageinfo) remplit une `IMAGEINFO` structure avec les informations relatives à une seule image, y compris les poignées des bitmaps d’image et de masque, le nombre de plans de couleur et de bits par pixel et le rectangle englobant de l’image dans la bitmap de l’image. Vous pouvez utiliser ces informations pour manipuler directement les bitmaps de l’image.

La fonction membre [GetImageCount](reference/cimagelist-class.md#getimagecount) récupère le nombre d’images dans une liste d’images.

Vous pouvez créer une icône basée sur une image et un masque dans une liste d’images à l’aide de la fonction membre [ExtractIcon](reference/cimagelist-class.md#extracticon) . La fonction retourne le handle de la nouvelle icône.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](using-cimagelist.md)<br/>
[Contrôles](controls-mfc.md)
