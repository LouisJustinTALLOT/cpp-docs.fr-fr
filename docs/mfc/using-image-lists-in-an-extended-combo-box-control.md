---
title: À l’aide de listes d’images dans un contrôle de zone de liste déroulante étendue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- image lists [MFC], combo boxes
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: dfff25fe-af70-47a2-8032-3901d1e6842d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c9a701871631fead48c22b1ffb2cbc3c386b960
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33383343"
---
# <a name="using-image-lists-in-an-extended-combo-box-control"></a>Utilisation de listes d'images dans un contrôle de zone de liste déroulante étendue
La fonction principale des contrôles de zone de liste déroulante étendue est la possibilité d’associer des images à partir d’une liste d’images à des éléments individuels d’un contrôle de zone de liste déroulante. Chaque élément est en mesure d’afficher trois images différentes : une pour l’état sélectionné, l’autre pour son état désélectionné et une troisième pour une image de superposition.  
  
 La procédure suivante associe une liste d’images à un contrôle de zone de liste déroulante étendue :  
  
### <a name="to-associate-an-image-list-with-an-extended-combo-box-control"></a>Pour associer une liste d’images avec un contrôle de zone de liste déroulante étendue  
  
1.  Construire une nouvelle liste d’images (ou utilisez un objet de liste d’images existant), à l’aide de la [CImageList](../mfc/reference/cimagelist-class.md) constructeur et stocker le pointeur résultant.  
  
2.  Initialiser le nouvel objet de liste d’images en appelant [CImageList::Create](../mfc/reference/cimagelist-class.md#create). Le code suivant est un exemple de cet appel.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#10](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_1.cpp)]  
  
3.  Ajoutez des images facultatives pour chaque état possible : sélectionné ou non sélectionnées et qu’un segment de recouvrement. Le code suivant ajoute trois images prédéfinies.  
  
     [!code-cpp[NVC_MFCControlLadenDialog#11](../mfc/codesnippet/cpp/using-image-lists-in-an-extended-combo-box-control_2.cpp)]  
  
4.  Associer la liste d’images avec le contrôle avec un appel à [CComboBoxEx::SetImageList](../mfc/reference/ccomboboxex-class.md#setimagelist).  
  
 Une fois que la liste d’images a été associée au contrôle, vous pouvez spécifier individuellement les images de que chaque élément utilisera dans les trois états possibles. Pour plus d’informations, consultez [définition des Images d’un élément individuel](../mfc/setting-the-images-for-an-individual-item.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Contrôles](../mfc/controls-mfc.md)

