---
title: À l’aide d’Image répertorie avec des contrôles Header | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- header controls [MFC], image lists
- CHeaderCtrl class [MFC], image lists
- image lists [MFC], header controls
ms.assetid: d5e9b310-6278-406c-909c-eefa09549a47
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2da3737b54c53903f8fc8ff30cccba6165cbde45
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33382777"
---
# <a name="using-image-lists-with-header-controls"></a>Utilisation de listes d'images avec des contrôles Header
Éléments d’en-tête ont la possibilité d’afficher une image dans un élément d’en-tête. Cette image, stockée dans une liste d’images associée est de 16 x 16 pixels et présente les mêmes caractéristiques que les icônes utilisées dans un contrôle list view. Pour implémenter ce comportement avec succès, vous devez d’abord créer et initialiser la liste d’images associez la liste de contrôle header et puis modifier les attributs de l’élément d’en-tête qui va afficher l’image.  
  
 La procédure suivante illustre les détails à l’aide d’un pointeur vers un contrôle header (`m_pHdrCtrl`) et un pointeur vers une liste d’images (`m_pHdrImages`).  
  
### <a name="to-display-an-image-in-a-header-item"></a>Pour afficher une image dans un élément d’en-tête  
  
1.  Construire une nouvelle liste d’images (ou utilisez un objet de liste d’images existant) à l’aide de la [CImageList](../mfc/reference/cimagelist-class.md) constructeur, en stockant le pointeur résultant.  
  
2.  Initialiser le nouvel objet de liste d’images en appelant [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Le code suivant est un exemple de cet appel.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#15](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_1.cpp)]  
  
3.  Ajouter les images de chaque élément d’en-tête. Le code suivant ajoute deux images prédéfinies.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#16](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_2.cpp)]  
  
4.  Associer la liste d’images avec le contrôle d’en-tête avec un appel à [CHeaderCtrl::SetImageList](../mfc/reference/cheaderctrl-class.md#setimagelist).  
  
5.  Modifier l’élément d’en-tête pour afficher une image à partir de la liste d’images associée. L’exemple suivant affecte la première image, à partir de `m_phdrImages`, sur le premier élément d’en-tête, `m_pHdrCtrl`.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#17](../mfc/codesnippet/cpp/using-image-lists-with-header-controls_3.cpp)]  
  
 Pour plus d’informations sur les valeurs de paramètre utilisées, consultez les informations pertinentes [CHeaderCtrl](../mfc/reference/cheaderctrl-class.md).  
  
> [!NOTE]
>  Il est possible d’avoir plusieurs contrôles à l’aide de la même liste d’images. Par exemple, dans un contrôle list view standard, il peut être une liste d’images (des images de 16 x 16 pixels) utilisée par la vue petite icône d’un contrôle list view et les éléments du contrôle list view.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CHeaderCtrl](../mfc/using-cheaderctrl.md)

