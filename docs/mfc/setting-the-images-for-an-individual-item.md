---
title: Définition des Images d’un élément individuel | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aec02a07de8fad2f9ad063295090be5ace4146e6
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36953800"
---
# <a name="setting-the-images-for-an-individual-item"></a>Définition des images d'un élément individuel
Les différents types d’images utilisée par l’élément de zone de liste déroulante étendue sont déterminés par les valeurs dans le *iImage*, *iSelectedImage*, et *transport* membres de le [ COMBOBOXEXITEM](http://msdn.microsoft.com/library/windows/desktop/bb775746) structure. Chaque valeur est l’index d’une image dans la liste d’images associée du contrôle. Par défaut, ces membres sont définis sur 0, le contrôle affiche pas d’image pour l’élément. Si vous souhaitez utiliser des images pour un élément spécifique, vous pouvez modifier la structure en conséquence, lors de l’insertion de l’élément de zone de liste déroulante ou en modifiant un élément de zone de liste déroulante existant.  
  
## <a name="setting-the-image-for-a-new-item"></a>Définition de l’Image pour un nouvel élément  
 Si vous insérez un nouvel élément, initialisez le *iImage*, *iSelectedImage*, et *transport* membres avec les valeurs appropriées de la structure, puis insérez l’élément avec un appel à [CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).  
  
 L’exemple suivant insère un nouvel élément de zone de liste déroulante étendue (`cbi`) dans le contrôle de zone de liste déroulante étendue (`m_comboEx`), fournissant des index pour les trois états d’image :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>Définition de l’Image d’un élément existant  
 Si vous modifiez un élément existant, vous devez travailler avec les *masque* membre d’un **COMBOBOXEXITEM** structure.  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>Pour modifier un élément existant pour utiliser des images  
  
1.  Déclarer une **COMBOBOXEXITEM** de la structure et définir le *masque* membre de données pour les valeurs vous intéressez lors de la modification.  
  
2.  À l’aide de cette structure, effectuez un appel à [CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem).  
  
3.  Modifier la *masque*, *iImage*, et *iSelectedImage* membres de la structure qui vient d’être retournée, en utilisant les valeurs appropriées.  
  
4.  Effectuez un appel à [CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem), en passant la structure modifiée.  
  
 L’exemple suivant illustre cette procédure en échangeant les images sélectionnés et du troisième élément de zone de liste déroulante étendue :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Contrôles](../mfc/controls-mfc.md)

