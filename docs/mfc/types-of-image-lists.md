---
title: Types de listes d'images
ms.date: 11/04/2016
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
ms.openlocfilehash: 939aad78b7cf8cca9c940bae11892d23dbb659cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180848"
---
# <a name="types-of-image-lists"></a>Types de listes d'images

Il existe deux types de listes d’images ([CImageList](../mfc/reference/cimagelist-class.md)) : non masquées et masquées. Une « liste d’image non masquée » se compose d’une image bitmap de couleur qui contient une ou plusieurs images. Une « liste d’images masquées » se compose de deux bitmaps de taille égale. Le premier est un bitmap de couleur qui contient les images, et le second est un bitmap monochrome qui contient une série de masques, un pour chaque image de la première bitmap.

Une des surcharges de la `Create` fonction membre prend un indicateur pour indiquer si la liste d’images est masquée. (Les autres surcharges créent des listes d’images masquées.)

Lorsqu’une image non masquée est dessinée, elle est simplement copiée dans le contexte de périphérique cible ; Autrement dit, elle est dessinée sur la couleur d’arrière-plan existante du contexte de périphérique. Lorsqu’une image masquée est dessinée, les bits de l’image sont combinés avec les bits du masque, produit généralement des zones transparentes dans l’image bitmap où la couleur d’arrière-plan du contexte de périphérique cible transparaît. Vous pouvez spécifier plusieurs styles de dessin lorsque vous dessinez une image masquée. Par exemple, vous pouvez spécifier que l’image sera tramée pour indiquer un objet sélectionné.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](../mfc/using-cimagelist.md)<br/>
[Contrôles](../mfc/controls-mfc.md)
