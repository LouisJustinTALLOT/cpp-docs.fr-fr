---
title: Création d’une boîte de dialogue (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.dialog
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 928432000fb9a6347433b78b224e15f07ce810d2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742646"
---
# <a name="creating-a-dialog-box-c"></a>Création d’une boîte de dialogue (C++)

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-new-dialog-box"></a>Pour créer une nouvelle boîte de dialogue

1. Dans [affichage des ressources](../windows/resource-view-window.md), avec le bouton droit de votre fichier .rc, puis choisissez **ajouter une ressource** dans le menu contextuel.

   > [!NOTE]
   > Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

1. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **boîte de dialogue** dans le **Type de ressource** liste, puis choisissez **New**.

   Si un signe plus (**+**) apparaît en regard du **boîte de dialogue** type de ressource, cela signifie que les modèles de boîte de dialogue sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

   La nouvelle boîte de dialogue s’ouvre dans le **boîte de dialogue** éditeur.

   Vous pouvez également [ouvrir les boîtes de dialogue existantes dans l’éditeur de boîte de dialogue Modifier](../windows/viewing-and-editing-resources-in-a-resource-editor.md).

## <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Pour créer une boîte de dialogue qu’un utilisateur ne peut pas quitter

Vous pouvez créer une boîte de dialogue d’exécution qu’un utilisateur ne peut pas quitter. Ce type de boîte de dialogue est utile pour les ouvertures de session et pour le verrouillage d’application ou de document.

1. Dans le volet **Propriétés** de la boîte de dialogue, affectez la valeur **false** à la propriété **Menu système**.

   Ce paramètre désactive le menu système de boîte de dialogue et **fermer** bouton.

1. Dans le formulaire de boîte de dialogue, supprimez les boutons **Annuler** et **OK** .

   Au moment de l’exécution, un utilisateur ne peuvent pas quitter une boîte de dialogue modale qui possède ces caractéristiques.

Pour activer le test de ce type de boîte de dialogue, la fonction de boîte de dialogue test détecte quand **ÉCHAP** est enfoncé. (**ÉCHAP** est également appelé la touche virtuelle VK_ESCAPE.) Quelle que soit la façon dont la boîte de dialogue est conçue de comportement au moment de l’exécution, vous pouvez terminer le mode de test en appuyant sur **ÉCHAP**.

> [!NOTE]
> Pour les applications MFC, pour créer une boîte de dialogue que les utilisateurs ne peuvent pas quitter, vous devez substituer le comportement par défaut de `OnOK` et `OnCancel` , car même si vous supprimez les boutons associés, la boîte de dialogue peut toujours être ignorée en appuyant sur  **Entrez** ou **ÉCHAP**.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Guide pratique pour créer une ressource](../windows/how-to-create-a-resource.md)<br/>
[Fichiers de ressources](../windows/resource-files-visual-studio.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)