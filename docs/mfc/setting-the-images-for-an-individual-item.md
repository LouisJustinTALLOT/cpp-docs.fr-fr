---
title: "Définition des Images d’un élément individuel | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- extended combo boxes [MFC], images
- images [MFC], combo box items
ms.assetid: bde83db8-23a7-4e35-837a-c86447d2c0af
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 4d9cb74c2290292f44b8c6c9b8797890e759f315
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="setting-the-images-for-an-individual-item"></a>Définition des images d'un élément individuel
Les différents types d’images utilisée par l’élément de zone de liste déroulante étendue sont déterminés par les valeurs dans le `iImage`, **iSelectedImage**, et **transport** membres de le [COMBOBOXEXITEM ](http://msdn.microsoft.com/library/windows/desktop/bb775746) structure. Chaque valeur est l’index d’une image dans la liste d’images associée du contrôle. Par défaut, ces membres sont définis sur 0, le contrôle affiche pas d’image pour l’élément. Si vous souhaitez utiliser des images pour un élément spécifique, vous pouvez modifier la structure en conséquence, lors de l’insertion de l’élément de zone de liste déroulante ou en modifiant un élément de zone de liste déroulante existant.  
  
## <a name="setting-the-image-for-a-new-item"></a>Définition de l’Image pour un nouvel élément  
 Si vous insérez un nouvel élément, initialisez le `iImage`, **iSelectedImage**, et **transport** membres avec les valeurs appropriées de la structure, puis insérez l’élément avec un appel à [ CComboBoxEx::InsertItem](../mfc/reference/ccomboboxex-class.md#insertitem).  
  
 L’exemple suivant insère un nouvel élément de zone de liste déroulante étendue (`cbi`) dans le contrôle de zone de liste déroulante étendue (`m_comboEx`), fournissant des index pour les trois états d’image :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#12](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_1.cpp)]  
  
## <a name="setting-the-image-for-an-existing-item"></a>Définition de l’Image d’un élément existant  
 Si vous modifiez un élément existant, vous devez travailler avec les **masque** membre d’un **COMBOBOXEXITEM** structure.  
  
#### <a name="to-modify-an-existing-item-to-use-images"></a>Pour modifier un élément existant pour utiliser des images  
  
1.  Déclarer une **COMBOBOXEXITEM** de la structure et définir le **masque** membre de données pour les valeurs vous intéressez lors de la modification.  
  
2.  À l’aide de cette structure, effectuez un appel à [CComboBoxEx::GetItem](../mfc/reference/ccomboboxex-class.md#getitem).  
  
3.  Modifier la **masque**, `iImage`, et **iSelectedImage** membres de la structure qui vient d’être retournée, en utilisant les valeurs appropriées.  
  
4.  Effectuez un appel à [CComboBoxEx::SetItem](../mfc/reference/ccomboboxex-class.md#setitem), en passant la structure modifiée.  
  
 L’exemple suivant illustre cette procédure en échangeant les images sélectionnés et du troisième élément de zone de liste déroulante étendue :  
  
 [!code-cpp[NVC_MFCControlLadenDialog#13](../mfc/codesnippet/cpp/setting-the-images-for-an-individual-item_2.cpp)]  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Contrôles](../mfc/controls-mfc.md)

