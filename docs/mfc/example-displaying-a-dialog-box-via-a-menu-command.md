---
title: 'Exemple : Affichage d’une boîte de dialogue via une commande de Menu | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20d355215388861a7bc2586c2c253cd551124809
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33347985"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Exemple : affichage d'une boîte de dialogue via une commande de menu
Cette rubrique contient des procédures pour :  
  
-   Affiche une boîte de dialogue modale via une commande de menu.  
  
-   Affiche une boîte de dialogue non modale via une commande de menu.  
  
 Les deux exemples de procédures sont pour les applications MFC et fonctionnent dans une application que vous créez avec le [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md).  
  
 Les procédures utilisent les noms et les valeurs suivantes :  
  
|Élément|Nom ou valeur|  
|----------|-------------------|  
|Application|Dialogue|  
|Commande de menu|Commande test du menu Affichage ; ID de commande = ID_VIEW_TEST|  
|Boîte de dialogue|Boîte de dialogue de test ; Classe = CTestDialog ; Fichier d’en-tête = TestDialog.h ; Variable = testdlg, ptestdlg|  
|Gestionnaire de commandes|OnViewTest|  
  
### <a name="to-display-a-modal-dialog-box"></a>Pour afficher une boîte de dialogue modale  
  
1.  Créer la commande de menu ; consultez [création de Menus ou les éléments de Menu](../windows/creating-a-menu.md).  
  
2.  Créer la boîte de dialogue consultez [à partir de l’éditeur de boîte de dialogue](../windows/creating-a-new-dialog-box.md).  
  
3.  Ajoutez une classe pour votre boîte de dialogue. Consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md) pour plus d’informations.  
  
4.  Dans **affichage de classes**, sélectionnez la classe de document (CDisplayDialogDoc). Dans la fenêtre **Propriétés** , cliquez sur le bouton **Événements** . Double-cliquez sur l’ID de la commande de menu (ID_VIEW_TEST) dans le volet gauche de la **propriétés** et sélectionnez **commande**. Dans le volet droit, cliquez sur la flèche vers le bas et sélectionnez  **\<Ajouter > OnViewTest**.  
  
     Si vous avez ajouté la commande de menu au macroordinateur d’une application MDI, sélectionnez la classe d’application (CDisplayDialogApp) à la place.  
  
5.  Ajoutez l’instruction à CDisplayDialogDoc.cpp (ou CDisplayDialogApp.cpp) include suivante après les instructions include existantes :  
  
     [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
6.  Ajoutez le code suivant à `OnViewTest` pour implémenter la fonction :  
  
     [!code-cpp[NVC_MFCControlLadenDialog#43](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_2.cpp)]  
  
### <a name="to-display-a-modeless-dialog-box"></a>Pour afficher une boîte de dialogue non modales  
  
1.  Effectuez les quatre premières étapes pour afficher la boîte de dialogue modale, mais sélectionnez la classe d’affichage (CDisplayDialogView) à l’étape 4.  
  
2.  Modifiez DisplayDialogView.h :  
  
    -   Déclarez la classe de boîte de dialogue précédant la déclaration de première classe :  
  
         [!code-cpp[NVC_MFCControlLadenDialog#44](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_3.h)]  
  
    -   Déclarer un pointeur vers la boîte de dialogue après la section publique attributs :  
  
         [!code-cpp[NVC_MFCControlLadenDialog#45](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_4.h)]  
  
3.  Modifiez DisplayDialogView.cpp :  
  
    -   Ajoutez que l’instruction include suivante après les instructions include existantes :  
  
         [!code-cpp[NVC_MFCControlLadenDialog#42](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_1.cpp)]  
  
    -   Ajoutez le code suivant au constructeur :  
  
         [!code-cpp[NVC_MFCControlLadenDialog#46](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_5.cpp)]  
  
    -   Ajoutez le code suivant au destructeur :  
  
         [!code-cpp[NVC_MFCControlLadenDialog#47](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_6.cpp)]  
  
    -   Ajoutez le code suivant à `OnViewTest` pour implémenter la fonction :  
  
         [!code-cpp[NVC_MFCControlLadenDialog#48](../mfc/codesnippet/cpp/example-displaying-a-dialog-box-via-a-menu-command_7.cpp)]  
  
 En outre, consultez l’article suivant de la Base de connaissances :  
  
-   Q251059 : Comment : fournir votre propre nom de classe de fenêtre pour la boîte de dialogue MFC  
  
## <a name="see-also"></a>Voir aussi  
 [Boîtes de dialogue](../mfc/dialog-boxes.md)   
 [Boîtes de dialogue modales et non modales](../mfc/modal-and-modeless-dialog-boxes.md)

