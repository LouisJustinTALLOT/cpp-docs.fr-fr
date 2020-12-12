---
description: 'En savoir plus sur : dessin d’images à partir d’une liste d’images'
title: Dessin d'images à partir d'une liste d'images
ms.date: 11/04/2016
helpviewer_keywords:
- CImageList class [MFC], drawing images from
- drawing [MFC], images from image lists
- image lists [MFC], drawing images from
- images [MFC], drawing
ms.assetid: 2f6063fb-1c28-45f8-a333-008c064db11c
ms.openlocfilehash: 2c413092e1e7568488a091acd2b0db175d03dab9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283457"
---
# <a name="drawing-images-from-an-image-list"></a>Dessin d'images à partir d'une liste d'images

Pour dessiner une image, utilisez la fonction membre [CImageList ::D RAW](reference/cimagelist-class.md#draw) . Spécifiez un pointeur vers un objet de contexte de périphérique, l’index de l’image à dessiner, l’emplacement dans le contexte de périphérique où dessiner l’image et un jeu d’indicateurs pour désigner le style de dessin.

Lorsque vous spécifiez le style de **ILD_TRANSPARENT** , `Draw` utilise un processus en deux étapes pour dessiner une image masquée. En premier lieu, il effectue une opération AND logique sur les bits de l'image et les bits du masque. Ensuite, il exécute une opération XOR logique sur les résultats de la première opération et les bits d'arrière-plan du contexte du périphérique de destination. Ce processus crée des zones transparentes dans l'image résultante ; autrement dit, chaque bit blanc dans le masque rend le bit correspondant dans l'image résultante transparent.

Avant de dessiner une image masquée sur un arrière-plan de couleur unie, vous devez utiliser la fonction membre [SetBkColor](reference/cimagelist-class.md#setbkcolor) pour définir la couleur d’arrière-plan de la liste d’images sur la même couleur que la destination. La définition de la couleur élimine la nécessité de créer des zones transparentes dans l’image et permet `Draw` à de copier simplement l’image dans le contexte de périphérique de destination, ce qui entraîne une augmentation significative des performances. Pour dessiner l’image, spécifiez le style de **ILD_NORMAL** lorsque vous appelez `Draw` .

Vous pouvez définir la couleur d’arrière-plan d’une liste d’images masquées ([CImageList](reference/cimagelist-class.md)) à tout moment pour qu’elle soit correctement dessinée sur un arrière-plan Uni. La définition de la couleur d’arrière-plan sur **CLR_NONE** entraîne le dessin par défaut des images de manière transparente. Pour récupérer la couleur d’arrière-plan d’une liste d’images, utilisez la fonction membre [GetBkColor](reference/cimagelist-class.md#getbkcolor) .

Les styles **ILD_BLEND25** et **ILD_BLEND50** dithernt l’image avec la couleur de surbrillance du système. Ces styles sont utiles si vous utilisez une image masquée pour représenter un objet que l'utilisateur peut sélectionner. Par exemple, vous pouvez utiliser le style **ILD_BLEND50** pour dessiner l’image lorsque l’utilisateur la sélectionne.

Une image non masquée est copiée dans le contexte de périphérique de destination à l’aide de l' `SRCCOPY` opération Raster. Les couleurs dans l'image s'affichent de la même façon indépendamment de la couleur d'arrière-plan du contexte de périphérique. Les styles de dessin spécifiés dans `Draw` n’ont pas non plus d’effet sur l’apparence d’une image non masquée.

Outre la fonction membre Draw, une autre fonction, [DrawIndirect](reference/cimagelist-class.md#drawindirect), permet d’étendre la capacité de rendu d’une image. `DrawIndirect` prend comme paramètre une structure [IMAGELISTDRAWPARAMS](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams) . Cette structure peut être utilisée pour personnaliser le rendu de l'image actuelle, notamment l'utilisation de codes d'opération de rastérisation (ROP, Raster Operation). Pour plus d’informations sur les codes ROP, consultez [codes d’opération Raster](/windows/win32/gdi/raster-operation-codes) et [bitmaps en tant que pinceaux](/windows/win32/gdi/bitmaps-as-brushes) dans le SDK Windows.

## <a name="see-also"></a>Voir aussi

[Utilisation de CImageList](using-cimagelist.md)<br/>
[Contrôles](controls-mfc.md)
