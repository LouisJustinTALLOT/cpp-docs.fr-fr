---
title: Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue (C++)
ms.date: 06/28/2018
helpviewer_keywords:
- Dialog Editor [C++], adding event handlers to controls
- controls [C++], event handlers
- dialog box controls [C++], events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
ms.openlocfilehash: e6539b7e0f8ab4d0b1b60ecfbd80685473534316
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487176"
---
# <a name="adding-event-handlers-for-dialog-box-controls-c"></a>Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue (C++)

Pour les boîtes de dialogue de projet qui sont déjà associés à une classe, vous pouvez tirer parti de certains raccourcis lorsque vous créez des gestionnaires d’événements. Vous pouvez rapidement créer un gestionnaire pour l’événement de notification de contrôle par défaut ou pour n’importe quel message Windows applicable.

### <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Pour créer un gestionnaire pour l’événement de notification de contrôle par défaut

1. Double-cliquez sur le contrôle. Le **texte** éditeur s’ouvre.

2. Ajoutez le code de gestionnaire de notification de contrôle dans le **texte** éditeur.

### <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Pour créer un gestionnaire pour n’importe quel message Windows applicable

1. Cliquez sur le contrôle pour lequel vous souhaitez gérer l’événement de notification.

2. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), cliquez sur le **ControlEvents** bouton pour afficher la liste des événements Windows communs associé au contrôle. Par exemple, la norme **OK** bouton sur le **sur** boîte de dialogue répertorie les événements de notification suivants :

   - BN_CLICKED

   - BN_DOUBLECLICKED

   - BN_KILLFOCUS

   - BN_SETFOCUS

   > [!NOTE]
   > Vous pouvez également sélectionner la boîte de dialogue et cliquez sur le **ControlEvents** bouton pour afficher la liste des événements Windows communs pour tous les contrôles dans la boîte de dialogue.

3. Dans le **propriétés** fenêtre, cliquez sur la colonne de droite en regard de l’événement à gérer, puis sélectionnez le nom d’événement de notification proposé (par exemple, `OnBnClickedOK` gère BN_CLICKED).

   > [!NOTE]
   > Alternativement, vous pouvez fournir un nom de gestionnaire d’événements de votre choix, plutôt que de sélectionner le nom de gestionnaire d’événements par défaut.

   Une fois que vous avez sélectionné l’événement, Visual Studio ouvre le **éditeur de texte** et affiche le code du Gestionnaire d’événements. Par exemple, le code suivant est ajouté pour la valeur par défaut `OnBnClickedOK`:

    ```cpp
    void CAboutDlg::OnBnClickedOk(void)
    {
        // TODO: Add your control notification handler code here
    }
    ```

Si vous souhaitez ajouter le Gestionnaire d’événements à une classe autre que celle qui implémente la boîte de dialogue, utilisez le [Assistant Gestionnaire d’événements](../ide/event-handler-wizard.md). Pour plus d’informations, consultez [Ajout d’un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Événements de contrôle par défaut](../windows/default-control-events.md)<br/>
[Définition de variables membres pour les contrôles de boîte de dialogue](../windows/defining-member-variables-for-dialog-controls.md)<br/>
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)<br/>
[Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)<br/>
[Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)<br/>
[Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)<br/>
[Substitution d’une fonction virtuelle](../ide/overriding-a-virtual-function-visual-cpp.md)<br/>
[Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)