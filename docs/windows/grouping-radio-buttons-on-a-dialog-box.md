---
title: Regroupement de cases d’option dans une boîte de dialogue | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.grouping
dev_langs:
- C++
helpviewer_keywords:
- member variables, adding to radio button groups
- variables, dialog box control member variables
- dialog box controls, grouping radio buttons
- grouping controls
- radio buttons, grouping on dialog boxes
ms.assetid: 3cc43f9e-56c8-4faa-9930-ce81733c69de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c3d0e20d8b2b88a7141672117d4c0b036682953e
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641416"
---
# <a name="grouping-radio-buttons-on-a-dialog-box"></a>Regroupement de cases d'option dans une boîte de dialogue
Lorsque vous ajoutez des cases d’option à une boîte de dialogue, traitez-les comme un groupe en définissant un **groupe** propriété dans le **propriétés** fenêtre pour le premier bouton dans le groupe. Un ID de contrôle pour cette case d’option apparaît alors dans [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), ce qui vous permet d’ajouter une variable membre pour le groupe de cases d’option.  
  
 Vous pouvez ajouter plusieurs groupes de cases d’option à une boîte de dialogue. Pour ajouter chaque groupe, appliquez la procédure suivante.  
  
### <a name="to-add-a-group-of-radio-buttons-to-a-dialog-box"></a>Pour ajouter un groupe de cases d’option à une boîte de dialogue  
  
1.  Sélectionnez le contrôle de case d’option dans la fenêtre [Boîte à outils](/visualstudio/ide/reference/toolbox) et cliquez sur l’emplacement dans la boîte de dialogue où vous souhaitez placer le contrôle.  
  
2.  Répétez l’étape 1 pour ajouter autant de cases d’option que vous le souhaitez. Assurez-vous que les cases d’option du groupe se suivent dans l’ordre de tabulation (pour plus d’informations, consultez [Modification de l’ordre de tabulation des contrôles](../windows/changing-the-tab-order-of-controls.md)).  
  
3.  Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), affectez la valeur **True** à la propriété *Groupe* de la **première**case d’option dans l’ordre de tabulation.  
  
     L’affectation de la valeur **True** à la propriété **Groupe** ajoute le style WS_GROUP à l’entrée du bouton dans l’objet de boîte de dialogue du script de ressources et permet de s’assurer qu’un utilisateur ne peut sélectionner qu’une case d’option à la fois dans le groupe de boutons (quand l’utilisateur clique sur une case d’option, les autres cases dans le groupe sont désactivées).  
  
    > [!NOTE]
    >  La propriété **Groupe** de la première case d’option du groupe doit avoir la valeur **True**. Si vous avez d’autres contrôles qui ne font pas partie du groupe de cases d’option, affectez aussi la valeur **True** à la propriété *Groupe* du premier contrôle **qui est en dehors du groupe** . Vous pouvez rapidement identifier le premier contrôle en dehors du groupe en appuyant sur **Ctrl**+**D** pour afficher l’ordre de tabulation.  
  
### <a name="to-add-a-member-variable-for-the-radio-button-group"></a>Pour ajouter une variable membre pour le groupe de cases d’option  
  
1.  Cliquez avec le bouton droit sur le premier contrôle de case d’option dans l’ordre de tabulation (le contrôle dominant et celui dont la propriété **Groupe** a la valeur True).  
  
2.  Choisissez **Ajouter une variable** dans le menu contextuel.  
  
3.  Dans l’ [Assistant Ajout de variable membre](../ide/add-member-variable-wizard.md), cochez la case **Variable de contrôle** , puis sélectionnez la case d’option **Valeur** .  
  
4.  Dans la zone **Nom de la variable** , tapez un nom pour la nouvelle variable membre.  
  
5.  Dans le **type de Variable** zone de liste, sélectionnez **int** ou type `int`.  
  
6.  Vous pouvez maintenant modifier votre code pour spécifier la case d’option qui doit apparaître sélectionnée. Par exemple, `m_radioBox1 = 0;` sélectionne le premier bouton de case d’option dans le groupe.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Disposition des contrôles sur les boîtes de dialogue](../windows/arrangement-of-controls-on-dialog-boxes.md)   
 [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)   
 [Contrôles](../mfc/controls-mfc.md)