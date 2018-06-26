---
title: Dessin d’Images à partir d’une liste d’images | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0ebc05a83eb22d494a75ed474e315112522af3fc
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36932066"
---
# <a name="drawing-images-from-an-image-list"></a>Dessin d'images à partir d'une liste d'images
Pour dessiner une image, utilisez la [CImageList::Draw](../mfc/reference/cimagelist-class.md#draw) fonction membre. Spécifiez un pointeur vers un objet de contexte de périphérique, l’index de l’image à dessiner, l’emplacement dans le contexte de périphérique où dessiner l’image et un jeu d’indicateurs pour désigner le style de dessin.  
  
 Lorsque vous spécifiez la **ILD_TRANSPARENT** style, `Draw` utilise un processus en deux étapes pour dessiner une image masquée. En premier lieu, il effectue une opération AND logique sur les bits de l'image et les bits du masque. Ensuite, il exécute une opération XOR logique sur les résultats de la première opération et les bits d'arrière-plan du contexte du périphérique de destination. Ce processus crée des zones transparentes dans l'image résultante ; autrement dit, chaque bit blanc dans le masque rend le bit correspondant dans l'image résultante transparent.  
  
 Avant de dessiner une image masquée sur un arrière-plan de couleur unie, vous devez utiliser le [SetBkColor](../mfc/reference/cimagelist-class.md#setbkcolor) fonction membre pour définir la couleur d’arrière-plan de la liste d’images à la même couleur que la destination. Définition de la couleur élimine le besoin de créer des zones transparentes dans l’image et permet `Draw` simplement copier l’image dans le contexte de périphérique de destination, ce qui entraîne une augmentation significative des performances. Pour dessiner l’image, spécifiez la **ILD_NORMAL** style lorsque vous appelez `Draw`.  
  
 Vous pouvez définir la couleur d’arrière-plan pour une liste d’images masquées ([CImageList](../mfc/reference/cimagelist-class.md)) à tout moment afin qu’elle correctement sur n’importe quel arrière-plan uni. Définition de la couleur d’arrière-plan sur **vous définissez CLR_NONE comme** entraîne des images à dessiner en toute transparence par défaut. Pour récupérer la couleur d’arrière-plan d’une liste d’images, utilisez le [GetBkColor](../mfc/reference/cimagelist-class.md#getbkcolor) fonction membre.  
  
 Le **ILD_BLEND25** et **ILD_BLEND50** styles font trembler l’image avec la couleur de surbrillance du système. Ces styles sont utiles si vous utilisez une image masquée pour représenter un objet que l'utilisateur peut sélectionner. Par exemple, vous pouvez utiliser la **ILD_BLEND50** style pour dessiner l’image lorsque l’utilisateur le sélectionne.  
  
 Une image non masquée est copiée dans le contexte de périphérique de destination à l’aide du `SRCCOPY` opération de rastérisation. Les couleurs dans l'image s'affichent de la même façon indépendamment de la couleur d'arrière-plan du contexte de périphérique. Les styles de dessin spécifiés dans `Draw` ont également aucun effet sur l’apparence d’une image non masquée.  
  
 En plus de la fonction membre Draw, une autre fonction, [DrawIndirect](../mfc/reference/cimagelist-class.md#drawindirect), étend la capacité d’afficher une image. `DrawIndirect` prend comme paramètre, un [IMAGELISTDRAWPARAMS](http://msdn.microsoft.com/library/windows/desktop/bb761395) structure. Cette structure peut être utilisée pour personnaliser le rendu de l'image actuelle, notamment l'utilisation de codes d'opération de rastérisation (ROP, Raster Operation). Pour plus d’informations sur les codes ROP, consultez [opération de rastérisation](http://msdn.microsoft.com/library/windows/desktop/dd162892) et [Bitmaps en tant que pinceaux](http://msdn.microsoft.com/library/windows/desktop/dd183378) dans le Kit de développement logiciel Windows.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CImageList](../mfc/using-cimagelist.md)   
 [Contrôles](../mfc/controls-mfc.md)

