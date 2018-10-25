---
title: 'Comment : ajouter la commande routage pour les Windows Forms contrôle | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 2af0148c386bc3b1ea8db60fdf84d080c38af857
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50080687"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>Comment : ajouter le routage des commandes au contrôle Windows Forms

[CWinFormsView](../mfc/reference/cwinformsview-class.md) achemine les commandes et les messages de l’interface utilisateur de commande de mise à jour vers le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu de frame et boutons de barre d’outils).

Le contrôle utilisateur utilise [ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize) pour stocker une référence à l’objet de source de commande dans `m_CmdSrc`, comme illustré dans l’exemple suivant. Pour utiliser `ICommandTarget` vous devez ajouter une référence à mfcmifc80.dll.

`CWinFormsView` gère plusieurs des notifications d’affichage MFC communes en les envoyant au contrôle utilisateur managé. Ces notifications incluent le [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate), [OnUpdate](../mfc/reference/iview-interface.md#onupdate) et [OnActivateView](../mfc/reference/iview-interface.md#onactivateview) méthodes.

Cette rubrique suppose que vous avez déjà effectué [Comment : créer le contrôle utilisateur et l’héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md) et [Comment : créer le contrôle utilisateur et l’hôte de l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

### <a name="to-create-the-mfc-host-application"></a>Pour créer l’application MFC hôte

1. Ouvrez la bibliothèque de contrôles Windows Forms vous avez créé dans [Comment : créer le contrôle utilisateur et l’héberger dans une boîte de dialogue](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md).

1. Ajoutez une référence à mfcmifc80.dll en cliquant sur le nœud du projet dans **l’Explorateur de solutions**, en sélectionnant **ajouter**, **référence**, puis accédez à Microsoft Visual Studio 10.0\VC\atlmfc\lib.

1. Ouvrez UserControl1.Designer.cs et ajoutez le code suivant à l’aide d’instruction :

    ```
    using Microsoft.VisualC.MFC;
    ```

1. En outre, dans UserControl1.Designer.cs, remplacez cette ligne :

    ```
    partial class UserControl1
    ```

   Par ceci :

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. Ajoutez-la comme la première ligne de la définition de classe pour `UserControl1`:

    ```
    private ICommandSource m_CmdSrc;
    ```

1. Ajoutez les définitions de méthode suivantes à `UserControl1` (nous créerons l’ID du contrôle MFC dans l’étape suivante) :

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

1. Ouvrez l’application MFC que vous avez créé dans [Comment : créer le contrôle utilisateur et l’hôte de l’affichage MDI](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md).

1. Ajoutez une option de menu qui appelle `singleMenuHandler`.

   Accédez à **affichage des ressources** (Ctrl + Maj + E), développez le **Menu** dossier, puis double-cliquez sur **IDR_MFC02TYPE**. Cela affiche l’éditeur de menus.

   Ajoutez une option de menu en bas de la **vue** menu. Notez l’ID de l’option de menu dans le **propriétés** fenêtre. Enregistrez le fichier.

   Dans **l’Explorateur de solutions**, ouvrez le fichier Resource.h, copiez la valeur d’ID pour l’option de menu que vous venez d’ajouter et collez cette valeur comme premier paramètre à la `m_CmdSrc.AddCommandHandler` appeler dans le projet c# `Initialize` (méthode) (en remplaçant `32771` si nécessaire).

9. Générez et exécutez le projet.

   Dans le menu **Générer** , cliquez sur **Générer la solution**.

   Sur le **déboguer** menu, cliquez sur **démarrer sans débogage**.

   Sélectionnez l’option de menu que vous avez ajouté. Notez que la méthode dans le fichier .dll est appelée.

## <a name="see-also"></a>Voir aussi

[Hébergement d’un contrôle utilisateur Windows Forms en tant que vue MFC](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource, interface](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget, interface](../mfc/reference/icommandtarget-interface.md)
