---
title: 'Comment : ajouter le routage des commandes au contrôle Windows Forms'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: ad64a12051c22a0cfca99d3ec9c5abef579902f4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365167"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Comment : ajouter le routage des commandes au contrôle Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) itinéraires commandes et mise à jour des messages d’interface utilisateur de commande au contrôle de l’utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu cadre et les boutons de barre d’outils).

Le contrôle de l’utilisateur utilise [ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) pour `m_CmdSrc`stocker une référence à l’objet source de commande, comme indiqué dans l’exemple suivant. Pour `ICommandTarget` utiliser, vous devez ajouter une référence à mfcmifc80.dll.

`CWinFormsView`gère plusieurs notifications de vue MFC courantes en les transmettant au contrôle de l’utilisateur géré. Ces notifications comprennent les méthodes [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) et [OnActivateView.](../mfc/reference/iview-interface.md#onactivateview)

Ce sujet suppose que vous avez déjà terminé [Comment : Créer le contrôle de l’utilisateur et l’hôte dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) et comment : Créer le contrôle utilisateur et [héberger la vue MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Créer l’application d’hôte MFC

1. Ouvrez windows Forms Control Library que vous avez créé dans [Comment : Créer le contrôle et l’hôte de l’utilisateur dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

1. Ajoutez une référence à mfcmifc80.dll, ce que vous pouvez faire en cliquant à droite sur le nœud du projet dans **Solution Explorer**, en sélectionnant **Add**, **Reference**, puis en naviguant vers Microsoft Visual Studio 10.0'VC’atlmfc’lib.

1. Ouvrez UserControl1.Designer.cs et ajoutez l’instruction suivante à l’aide de :

    ```
    using Microsoft.VisualC.MFC;
    ```

1. En outre, dans UserControl1.Designer.cs, changer cette ligne:

    ```
    partial class UserControl1
    ```

   par ceci :

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Ajoutez ceci comme la première ligne `UserControl1`de la définition de classe pour :

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Ajouter les définitions `UserControl1` de méthode suivantes à (nous allons créer l’ID du contrôle MFC dans la prochaine étape):

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

1. Ouvrez l’application MFC que vous avez créée dans [Comment : Créer le contrôle utilisateur et héberger MDI View](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Ajouter une option de `singleMenuHandler`menu qui invoquera .

   Rendez-vous sur **Resource View** (Ctrl-Shift-E), élargissez le dossier **menu,** puis double clic **IDR_MFC02TYPE**. Cela affiche l’éditeur du menu.

   Ajoutez une option de menu au bas du menu **View.** Remarquez l’id de l’option de menu dans la fenêtre **Propriétés.** Enregistrez le fichier .

   Dans **Solution Explorer**, ouvrez le fichier Resource.h, copiez la valeur d’identification pour l’option de menu que vous venez d’ajouter, et collez cette valeur comme premier paramètre de l’appel `m_CmdSrc.AddCommandHandler` dans la méthode du `Initialize` projet C (remplacement `32771` si nécessaire).

1. Générez et exécutez le projet.

   Dans le menu **Générer**, cliquez sur **Générer la solution**.

   Sur le menu **Debug,** cliquez sur **Démarrer sans débogage**.

   Sélectionnez l’option de menu que vous avez ajoutée. Notez que la méthode dans le .dll est appelé.

## <a name="see-also"></a>Voir aussi

[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource Interface](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget Interface](../mfc/reference/icommandtarget-interface.md)
