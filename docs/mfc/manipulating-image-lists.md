---
title: Manipulation de listes d’images | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], manipulating
- lists [MFC], image
- CImageList class [MFC], manipulating
ms.assetid: 043418f8-077e-4dce-b8bb-2b7b0d7b5156
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1eeccfa5245c6395e530859eb91c7f9a5c01335e
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930369"
---
# <a name="manipulating-image-lists"></a>Manipulation de listes d'images
Le [remplacer](../mfc/reference/cimagelist-class.md#replace) fonction membre remplace une image dans une liste d’images ([CImageList](../mfc/reference/cimagelist-class.md)) avec une nouvelle image. Cette fonction est également utile si vous devez augmenter de façon dynamique le nombre d’images dans un objet de liste d’images. Le [fonction SetImageCount](../mfc/reference/cimagelist-class.md#setimagecount) fonction modifie dynamiquement le nombre d’images stockées dans la liste d’images. Si vous augmentez la taille de la liste d’images, appelez `Replace` pour ajouter des images aux nouveaux emplacements. Si vous réduisez la taille de la liste d’images, les images au-delà de la nouvelle taille sont libérées.  
  
 Le [supprimer](../mfc/reference/cimagelist-class.md#remove) fonction membre supprime d’une image à partir d’une liste d’images. Le [copie](../mfc/reference/cimagelist-class.md#copy) fonction membre peut copier ou permuter des images dans une liste d’images. Cette fonction vous permet d’indiquer si l’image source doit être copié à l’index de destination ou les images de la source et de destination doivent être échangées.  
  
 Pour créer une nouvelle liste d’images en fusionnant les deux listes d’images, utilisez la surcharge appropriée de la [créer](../mfc/reference/cimagelist-class.md#create) fonction membre. Cette surcharge de `Create` fusions répertorie de la première image de l’image existante, le stockage de l’image résultante dans un nouvel objet de liste d’images. La nouvelle image est créée en dessinant la deuxième image transparente sur la première. Le masque de la nouvelle image est le résultat d’une opération OR logique sur les bits des masques pour les deux images existantes.  
  
 Cette opération est répétée jusqu'à ce que toutes les images sont fusionnées et ajoutées au nouvel objet de liste d’images.  
  
 Vous pouvez écrire les informations de l’image dans une archive en appelant le [écrire](../mfc/reference/cimagelist-class.md#write) fonction membre et en lecture en appelant le [en lecture](../mfc/reference/cimagelist-class.md#read) fonction membre.  
  
 Le [fonctions membres GetSafeHandle](../mfc/reference/cimagelist-class.md#getsafehandle), [attacher](../mfc/reference/cimagelist-class.md#attach), et [détachement](../mfc/reference/cimagelist-class.md#detach) fonctions membres permettent de manipuler le descripteur de la liste d’images attachée à la `CImageList` objet, tandis que le [DeleteImageList](../mfc/reference/cimagelist-class.md#deleteimagelist) fonction membre supprime la liste d’images sans détruire le `CImageList` objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CImageList](../mfc/using-cimagelist.md)   
 [Contrôles](../mfc/controls-mfc.md)

