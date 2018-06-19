---
title: Création d’un contrôle de zone de liste déroulante étendue | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7c6a891aeadf2fa8366eec52a967e13776db6523
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33341210"
---
# <a name="creating-an-extended-combo-box-control"></a>Création d'un contrôle de zone de liste déroulante étendue
Comment le contrôle de zone de liste déroulante étendue est créé dépend de l’utilisation du contrôle dans une boîte de dialogue ou de la créer dans un autre type de fenêtre.  
  
### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>Pour utiliser CComboBoxEx directement dans une boîte de dialogue  
  
1.  Dans l’éditeur de boîte de dialogue, ajoutez un contrôle Extended Combo Box à votre ressource de modèle de boîte de dialogue. Spécifier son ID de contrôle.  
  
2.  Spécifiez les styles nécessaires, à l’aide de la boîte de dialogue Propriétés du contrôle de zone de liste déroulante étendue.  
  
3.  Utilisez le [Assistant Ajout de Variable membre](../ide/adding-a-member-variable-visual-cpp.md) pour ajouter une variable membre de type [CComboBoxEx](../mfc/reference/ccomboboxex-class.md) avec la propriété du contrôle. Vous pouvez utiliser ce membre pour appeler `CComboBoxEx` fonctions membres.  
  
4.  Utilisez la fenêtre Propriétés pour mapper des fonctions de gestionnaire de la classe de boîte de dialogue pour tout message notification du contrôle de zone de liste déroulante étendue vous devez gérer (consultez [mappage de Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md)).  
  
5.  Dans [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog), définissez d’autres styles pour le `CComboBoxEx` objet.  
  
### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>Pour utiliser CComboBoxEx dans un autre type de fenêtre  
  
1.  Définissez le contrôle dans la classe d’affichage ou de la fenêtre.  
  
2.  Appel du contrôle [créer](../mfc/reference/ctabctrl-class.md#create) fonction membre, éventuellement dans [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate), éventuellement en même temps que la fenêtre parente [OnCreate](../mfc/reference/cwnd-class.md#oncreate) fonction gestionnaire. Définissez les styles pour le contrôle.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Contrôles](../mfc/controls-mfc.md)

