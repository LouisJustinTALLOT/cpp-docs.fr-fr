---
title: À l’aide d’une liste d’images | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- lists [MFC], image
- CImageList class [MFC], using
- image lists [MFC]
ms.assetid: e0aed188-a1e6-400e-9f51-033d61c5541f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5722a2ef8c4e93e4996ee243b3c01b6dd6aeca78
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33381603"
---
# <a name="using-an-image-list"></a>Utilisation d'une liste d'images
L’utilisation typique d’une liste d’images suit le modèle suivant :  
  
-   Construire un [CImageList](../mfc/reference/cimagelist-class.md) de l’objet et appelez l’une des surcharges de son [créer](../mfc/reference/cimagelist-class.md#create) fonction pour créer une liste d’images et l’attacher à la `CImageList` objet.  
  
-   Si vous n’avez pas ajouter des images lorsque vous avez créé la liste d’images, ajouter des images à la liste d’images en appelant le [ajouter](../mfc/reference/cimagelist-class.md#add) ou [en lecture](../mfc/reference/cimagelist-class.md#read) fonction membre.  
  
-   Associer la liste d’images à un contrôle en appelant la fonction membre approprié de ce contrôle ou de dessiner des images à partir de la liste d’images à l’aide de la liste d’images [dessiner](../mfc/reference/cimagelist-class.md#draw) fonction membre.  
  
-   Peut-être autoriser l’utilisateur à faire glisser une image à l’aide de la prise en charge intégrée de la liste d’images en faisant glisser.  
  
> [!NOTE]
>  Si la liste d’images a été créée avec le **nouveau** (opérateur), vous devez détruire le `CImageList` lorsque vous avez terminé de l’objet.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CImageList](../mfc/using-cimagelist.md)   
 [Contrôles](../mfc/controls-mfc.md)

