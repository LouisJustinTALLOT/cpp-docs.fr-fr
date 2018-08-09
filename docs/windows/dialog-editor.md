---
title: Boîte de dialogue Éditeur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.dialog
- vc.editors.dialog.F1
dev_langs:
- C++
helpviewer_keywords:
- resource editors, Dialog editor
- editors, dialog boxes
- Dialog editor
- dialog boxes, editing
ms.assetid: d94884ef-2cca-49d8-9b58-775f34848134
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8c2f5339237bec053df6bf26fb161854f83f572a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39651848"
---
# <a name="dialog-editor"></a>Éditeur de boîtes de dialogue
Le **boîte de dialogue** éditeur vous permet de créer ou modifier des ressources de boîte de dialogue. Vous ouvrez l’éditeur de boîtes de dialogue en double-cliquant sur le fichier .rc d’une boîte de dialogue le **affichage des ressources** fenêtre (**vue** > **affichage des ressources**). Notez que **affichage des ressources** n’est pas disponible dans les éditions Express.  
  
 L'une des premières étapes de la création d'une boîte de dialogue (ou d'un modèle de boîte de dialogue) consiste à ajouter des contrôles à la boîte de dialogue. Dans le **boîte de dialogue** éditeur, vous pouvez organiser les contrôles pour s’ajuster à une certaine taille, forme ou alignement, ou vous pouvez les déplacer pour travailler dans la boîte de dialogue. Vous pouvez aussi facilement supprimer un contrôle.  
  
 Vous pouvez stocker une boîte de dialogue en tant que modèle pour pouvoir la réutiliser. Vous pouvez aussi facilement basculer entre la conception de la boîte de dialogue et la modification du code qui l'implémente.  
  
 Il est également possible de modifier les propriétés d'un ou plusieurs contrôles dans l'Éditeur de boîtes de dialogue. Vous pouvez modifier l’ordre de tabulation, autrement dit, l’ordre dans lequel les contrôles obtiennent focus lorsque la **onglet** touche est enfoncée ou vous pouvez définir une clé d’accès (une combinaison de touches) qui permet aux utilisateurs de choisir un contrôle à l’aide du clavier. Pour obtenir une liste des touches d'accès rapide prédéfinies, consultez [Touches accélérateur pour l'Éditeur de boîtes de dialogue](../windows/accelerator-keys-for-the-dialog-editor.md).  
  
 Le **boîte de dialogue** éditeur vous permet également d’utiliser des contrôles personnalisés, notamment des contrôles ActiveX. En outre, vous pouvez modifier un [mode formulaire](../mfc/reference/cformview-class.md), des [vues d'enregistrements](../data/record-views-mfc-data-access.md)ou des [barres de boîte de dialogue](../mfc/dialog-bars.md).  
  
 À compter de Visual Studio 2015, vous pouvez utiliser l’éditeur de boîtes de dialogue pour définir des dispositions dynamiques qui spécifient comment les contrôles déplacent et redimensionnent lorsque l’utilisateur redimensionne une boîte de dialogue. Pour plus d’informations, consultez [Dynamic Layout](../mfc/dynamic-layout.md).  
  
-   [Création d’une nouvelle boîte de dialogue](../windows/creating-a-new-dialog-box.md)  
  
-   [Création d’une boîte de dialogue que les utilisateurs ne peuvent pas quitter au moment de l’exécution](../windows/creating-a-dialog-box-that-users-cannot-exit.md)  
  
-   [Affichage ou masquage de la barre d’outils Éditeur de boîtes de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)  
  
-   [Basculement entre l’Éditeur de boîtes de dialogue et le code](../windows/switching-between-dialog-box-controls-and-code.md)  
  
-   [Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)  
  
-   [Ajout de gestionnaires d’événements pour les contrôles de boîte de dialogue](../windows/adding-event-handlers-for-dialog-box-controls.md)  
  
-   [Test d’une boîte de dialogue](../windows/testing-a-dialog-box.md)  
  
-   [Touches accélérateur pour l'Éditeur de boîtes de dialogue](../windows/accelerator-keys-for-the-dialog-editor.md)  
  
-   [Dépannage de l’Éditeur de boîtes de dialogue](../windows/troubleshooting-the-dialog-editor.md)  
  
    > [!TIP]
    >  Lors de l’utilisation du **boîte de dialogue** éditeur, dans de nombreux cas, vous pouvez cliquer sur le bouton droit de la souris pour afficher un menu contextuel des commandes fréquemment utilisées.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeurs de ressources](../windows/resource-editors.md)   
 [Contrôles](../mfc/controls-mfc.md)   
 [Classes de contrôle](../mfc/control-classes.md)   
 [Classes de boîte de dialogue](../mfc/dialog-box-classes.md)   
 [Contrôles de boîtes de dialogue et types de variables](../ide/dialog-box-controls-and-variable-types.md)