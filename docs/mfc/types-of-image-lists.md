---
title: Types de listes d’images | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- image lists [MFC], types of
- CImageList class [MFC], types
ms.assetid: bee5e7c3-78f5-4037-a136-9c50d67cdee5
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 580969195de9241d935e1c27e1659f6e0c4c40ab
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953206"
---
# <a name="types-of-image-lists"></a>Types de listes d'images
Il existe deux types de listes d’images ([CImageList](../mfc/reference/cimagelist-class.md)) : non masquées et masquées. Une « liste d’image non masquée » se compose d’une image bitmap de couleur qui contient une ou plusieurs images. Une « liste d’images masquées » se compose de deux bitmaps de taille égale. Le premier est une image bitmap de couleur qui contient les images, et le second est un bitmap monochrome contenant une série de masques, un pour chaque image de la première bitmap.  
  
 Une des surcharges de la `Create` fonction membre prend un indicateur pour indiquer si la liste d’images est masquée. (Les autres surcharges de créent des listes d’images masquées.)  
  
 Lorsqu’une image non masquée est dessinée, elle est simplement copiée dans le contexte de périphérique cible ; Autrement dit, elle est dessinée sur la couleur d’arrière-plan existante du contexte de périphérique. Lorsqu’une image masquée est dessinée, les bits de l’image sont combinés avec les bits du masque, produit généralement où la couleur d’arrière-plan du contexte de périphérique cible apparaît à travers les zones transparentes dans l’image bitmap. Vous pouvez spécifier plusieurs styles de dessin lorsque vous dessinez une image masquée. Par exemple, vous pouvez spécifier que l’image sera tramée pour indiquer un objet sélectionné.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CImageList](../mfc/using-cimagelist.md)   
 [Contrôles](../mfc/controls-mfc.md)

