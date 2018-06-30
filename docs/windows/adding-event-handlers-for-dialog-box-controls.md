---
title: Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue | Documents Microsoft
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Dialog editor, adding event handlers to controls
- controls [C++], event handlers
- dialog box controls, events
- event handlers, for dialog box controls
ms.assetid: f9c70f24-ea6f-44df-82eb-78a2deaee769
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bb39e502ccc40531e72f761a414e4088de8b147d
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2018
ms.locfileid: "37121120"
---
# <a name="adding-event-handlers-for-dialog-box-controls"></a>Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue

Pour les boîtes de dialogue de projet qui sont déjà associés à une classe, vous pouvez tirer parti de certains raccourcis lorsque vous créez des gestionnaires d’événements. Vous pouvez rapidement créer un gestionnaire pour l’événement de notification de contrôle par défaut ou pour les messages Windows applicables.

## <a name="to-create-a-handler-for-the-default-control-notification-event"></a>Pour créer un gestionnaire pour l’événement de notification de contrôle par défaut

1. Double-cliquez sur le contrôle. L’éditeur de texte s’ouvre.

2. Ajoutez le code de gestionnaire de notification de contrôle dans l’éditeur de texte.

## <a name="to-create-a-handler-for-any-applicable-windows-message"></a>Pour créer un gestionnaire pour les messages Windows applicables

1. Cliquez sur le contrôle pour lequel vous souhaitez gérer l’événement de notification.

2. Dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), cliquez sur le **ControlEvents** bouton pour afficher la liste des événements Windows courants, associé au contrôle. Par exemple, la norme **OK** bouton sur le **sur** boîte de dialogue répertorie les événements de notification suivants :

   - **BN_CLICKED**

   - **BN_DOUBLECLICKED**

   - **BN_KILLFOCUS**

   - **BN_SETFOCUS**

    > [!NOTE]
    > Vous pouvez également sélectionner la boîte de dialogue et cliquez sur le **ControlEvents** bouton pour afficher la liste des événements Windows courants pour tous les contrôles dans la boîte de dialogue.

3. Dans le **propriétés** fenêtre, cliquez sur la colonne de droite en regard de l’événement à gérer, puis sélectionnez le nom d’événement de notification proposé (par exemple, **OnBnClickedOK** handles **BN_CLICKED** ).

    > [!NOTE]
    > Ou bien, vous pouvez fournir un nom de gestionnaire d’événements de votre choix, plutôt que de sélectionner le nom de gestionnaire d’événements par défaut.

   Une fois que vous avez sélectionné l’événement, Visual Studio ouvre l’éditeur de texte et affiche le code du Gestionnaire d’événements. Par exemple, le code suivant est ajouté pour la valeur par défaut **OnBnClickedOK**:

    ```cpp
    void CAboutDlg::OnBnClickedOk(void)
    {
        // TODO: Add your control notification handler code here
    }
    ```

Si vous souhaitez ajouter le Gestionnaire d’événements à une classe autre que celle qui implémente la boîte de dialogue, utilisez le [Assistant Gestionnaire d’événements](../ide/event-handler-wizard.md). Pour plus d’informations, consultez [Ajout d’un gestionnaire d’événements](../ide/adding-an-event-handler-visual-cpp.md).

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

### <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Événements de contrôle par défaut](../windows/default-control-events.md)  
[Définition de variables membres pour les contrôles de boîte de dialogue](../windows/defining-member-variables-for-dialog-controls.md)  
[Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)  
[Ajout d’une classe](../ide/adding-a-class-visual-cpp.md)  
[Ajout d’une fonction membre](../ide/adding-a-member-function-visual-cpp.md)  
[Ajout d’une variable membre](../ide/adding-a-member-variable-visual-cpp.md)  
[Une fonction virtuelle de substitution](../ide/overriding-a-virtual-function-visual-cpp.md)  
[Gestionnaire de messages MFC](../mfc/reference/adding-an-mfc-message-handler.md)  
