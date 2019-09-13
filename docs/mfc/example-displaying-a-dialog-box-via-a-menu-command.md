---
title: 'Exemple : Affichage d’une boîte de dialogue via une commande de menu'
ms.date: 09/07/2019
helpviewer_keywords:
- MFC dialog boxes [MFC], examples
- MFC dialog boxes [MFC], displaying
- modeless dialog boxes [MFC], displaying
- dialog boxes [MFC], MFC
- modal dialog boxes [MFC], displaying
- examples [MFC], dialog boxes
- menu items [MFC], examples
ms.assetid: e8692549-acd7-478f-9c5e-ba310ce8cccd
ms.openlocfilehash: 9b76d481bff6e98b915d71634dbf04a83a432736
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907743"
---
# <a name="example-displaying-a-dialog-box-via-a-menu-command"></a>Exemple : Affichage d’une boîte de dialogue via une commande de menu

Cette rubrique contient des procédures pour :

- Afficher une boîte de dialogue modale à l’aide d’une commande de menu.

- Affiche une boîte de dialogue non modale via une commande de menu.

Les deux exemples de procédures concernent les applications MFC et fonctionnent dans une application que vous créez à l’aide de l' [Assistant Application MFC](../mfc/reference/mfc-application-wizard.md).

Les procédures utilisent les noms et valeurs suivants :

|Item|Nom ou valeur|
|----------|-------------------|
|Application|DisplayDialog|
|Commande de menu|Commande test dans le menu Affichage ; ID de commande = ID_VIEW_TEST|
|Boîte de dialogue|Boîte de dialogue test ; Class = CTestDialog ; Fichier d’en-tête = TestDialog. h ; Variable = testdlg, ptestdlg|
|Gestionnaire de commandes|OnViewTest|

### <a name="to-display-a-modal-dialog-box"></a>Pour afficher une boîte de dialogue modale

1. Créez la commande de menu. consultez [création de menus ou d’éléments de menu](../windows/creating-a-menu.md).

1. Créer la boîte de dialogue ; consultez [démarrage de l’éditeur de boîtes de dialogue](../windows/creating-a-new-dialog-box.md).

1. Ajoutez une classe pour votre boîte de dialogue. Pour plus d’informations, consultez [Ajout d’une classe](../ide/adding-a-class-visual-cpp.md) .

1. Dans **affichage de classes**, sélectionnez la classe de document (CDisplayDialogDoc). Dans la fenêtre **Propriétés** , cliquez sur le bouton **Événements** . Double-cliquez sur l’ID de la commande de menu (ID_VIEW_TEST). Ensuite, cliquez sur la flèche orientée vers le bas et sélectionnez  **\<Ajouter > OnViewTest**.

   Si vous avez ajouté la commande de menu au macroordinateur d’une application MDI, sélectionnez la classe d’application (CDisplayDialogApp) à la place.

1. Ajoutez l’instruction include suivante à CDisplayDialogDoc. cpp (ou CDisplayDialogApp. cpp) après les instructions include existantes :

   ```cpp
   #include "TestDialog.h"
   ```

1. Ajoutez le code suivant à `OnViewTest` pour implémenter la fonction :

   ```cpp
   CTestDialog testdlg;
   testdlg.DoModal();  
   ```

### <a name="to-display-a-modeless-dialog-box"></a>Pour afficher une boîte de dialogue non modale

1. Effectuez les quatre premières étapes pour afficher une boîte de dialogue modale, à l’exception de la sélection de la classe d’affichage (CDisplayDialogView) à l’étape 4.

1. Modifiez DisplayDialogView. h :

   - Déclarez la classe de boîte de dialogue précédant la première déclaration de classe :

   ```cpp
   class CTestDialog;
   ```

   - Déclarez un pointeur vers la boîte de dialogue après la section des attributs publics :

   ```cpp
   CTestDialog* m_pTestDlg;
   ```

1. Modifiez DisplayDialogView. cpp :

   - Ajoutez l’instruction include suivante après les instructions include existantes :

   ```cpp
   #include "TestDialog.h"
   ```

   - Ajoutez le code suivant au constructeur :

   ```cpp
   m_pTestDlg = NULL;
   ```

   - Ajoutez le code suivant au destructeur :

   ```cpp
   delete m_pTestDlg;
   ```

   - Ajoutez le code suivant à `OnViewTest` pour implémenter la fonction :

   ```cpp
   if (NULL == m_pTestDlg)
   {
      m_pTestDlg = new CTestDialog(this);
      m_pTestDlg->Create(CTestDialog::IDD, this);
   }
   m_pTestDlg->ShowWindow(SW_SHOW); 
   ```

## <a name="see-also"></a>Voir aussi

[Boîtes de dialogue](../mfc/dialog-boxes.md)<br/>
[Boîtes de dialogue modales et non modales](../mfc/modal-and-modeless-dialog-boxes.md)
