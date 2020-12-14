---
description: 'En savoir plus sur : types de listes d’images'
title: Types de listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: be18a523db366813a236fd4fd94bbb001345f0d1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263736"
---
# <a name="types-of-image-lists"></a>Types de listes d'images

Il existe deux types de listes d’images ([CImageList](../mfc/reference/cimagelist-class.md)) : non masqué et masqué. Une « liste d’images non masquées » se compose d’une image bitmap de couleur qui contient une ou plusieurs images. Une « liste d’images masquées » est constituée de deux bitmaps de taille égale. La première est une image bitmap de couleur qui contient les images, tandis que la seconde est une image bitmap monochrome qui contient une série de masques, un pour chaque image de la première bitmap.

L’une des surcharges de la `Create` fonction membre prend un indicateur pour indiquer si la liste d’images est masquée ou non. (Les autres surcharges créent des listes d’images masquées.)

Lorsqu’une image non masquée est dessinée, elle est simplement copiée dans le contexte de périphérique cible ; autrement dit, il est dessiné sur la couleur d’arrière-plan existante du contexte de périphérique. Quand une image masquée est dessinée, les bits de l’image sont combinés avec les bits du masque, ce qui produit généralement des zones transparentes dans la bitmap où la couleur d’arrière-plan du contexte de périphérique cible s’affiche. Vous pouvez spécifier plusieurs styles de dessin lors du dessin d’une image masquée. Par exemple, vous pouvez spécifier que l’image soit pour indiquer un objet sélectionné.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
