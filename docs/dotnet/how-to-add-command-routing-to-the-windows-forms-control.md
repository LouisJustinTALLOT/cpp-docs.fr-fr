---
description: 'En savoir plus sur : Comment : ajouter le routage des commandes au contrôle Windows Forms'
title: 'Comment : ajouter le routage des commandes au contrôle Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: b46087d7df3da5f402432731db4b994b257a385b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335420"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Comment : ajouter le routage des commandes au contrôle Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) achemine les commandes et les messages de l’interface utilisateur de commande de mise à jour au contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu Frame et les boutons de barre d’outils).

Le contrôle utilisateur utilise [ICommandTarget :: Initialize](../mfc/reference/icommandtarget-interface.md#initialize) pour stocker une référence à l’objet source de la commande dans `m_CmdSrc` , comme illustré dans l’exemple suivant. Pour utiliser `ICommandTarget` , vous devez ajouter une référence à mfcmifc80.dll.

`CWinFormsView` gère plusieurs des notifications d’affichage MFC courantes en les transférant au contrôle utilisateur managé. Ces notifications incluent les méthodes [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) et [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) .

Cette rubrique part du principe que vous avez déjà terminé [Comment : créer le contrôle utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) et [Comment : créer le contrôle utilisateur et héberger l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application hôte MFC

1. Ouvrez Windows Forms bibliothèque de contrôles que vous avez créée dans [Comment : créer le contrôle utilisateur et l’hôte dans une](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)boîte de dialogue.

1. Ajoutez une référence à mfcmifc80.dll, ce que vous pouvez faire en cliquant avec le bouton droit sur le nœud du projet dans **Explorateur de solutions**, en sélectionnant **Ajouter**, **référence**, puis en accédant à Microsoft Visual Studio 10.0 \ VC\atlmfc\lib.

1. Ouvrez UserControl1.Designer.cs et ajoutez l’instruction using suivante :

    ```
    using Microsoft.VisualC.MFC;
    ```

1. En outre, dans UserControl1.Designer.cs, modifiez cette ligne :

    ```
    partial class UserControl1
    ```

   par ceci :

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Ajoutez-la en tant que première ligne de la définition de classe pour `UserControl1` :

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Ajoutez les définitions de méthode suivantes à `UserControl1` (nous allons créer l’ID du contrôle MFC à l’étape suivante) :

    ```
    public void Initialize (ICommandSource cmdSrc)
    {
       m_CmdSrc = cmdSrc;
       // need ID of control in MFC dialog and callback function
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));
    }

    private void singleMenuHandler (uint cmdUI)
    {
       // User command handler code
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");
    }
    ```

1. Ouvrez l’application MFC que vous avez créée dans [How to : Create the User Control and Host MDI View](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Ajoutez une option de menu qui appellera `singleMenuHandler` .

   Accédez à **affichage des ressources** (Ctrl + Maj + E), développez le dossier **menu** , puis double-cliquez sur **IDR_MFC02TYPE**. L’éditeur de menus s’affiche.

   Ajoutez une option de menu en bas du menu **affichage** . Notez l’ID de l’option de menu dans la fenêtre **Propriétés** . Enregistrez le fichier .

   Dans **Explorateur de solutions**, ouvrez le fichier Resource. h, copiez la valeur ID de l’option de menu que vous venez d’ajouter, puis collez cette valeur en tant que premier paramètre de l' `m_CmdSrc.AddCommandHandler` appel dans la méthode du projet C# `Initialize` (en remplaçant `32771` si nécessaire).

1. Générez et exécutez le projet.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Dans le menu **Déboguer** , cliquez sur **exécuter sans débogage**.

   Sélectionnez l’option de menu que vous avez ajoutée. Notez que la méthode dans le fichier. dll est appelée.

## <a name="see-also"></a>Voir aussi

[Hébergement d'un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[Interface ICommandSource](../mfc/reference/icommandsource-interface.md)<br/>
[Interface ICommandTarget](../mfc/reference/icommandtarget-interface.md)
