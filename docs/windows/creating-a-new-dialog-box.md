---
description: 'En savoir plus sur : Comment : créer une boîte de dialogue (C++)'
title: 'Comment : créer une boîte de dialogue (C++)'
ms.date: 02/15/2019
helpviewer_keywords:
- dialog boxes [C++], creating
- Dialog Editor [C++], creating dialog boxes
- modal dialog boxes [C++], logon screens
- logon screens
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 303de801-c4f8-42e1-b622-353f6423f688
ms.openlocfilehash: 8c02d0d85d20b51c867b3f3ba0e5f945595ed130
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97329491"
---
# <a name="how-to-create-a-dialog-box-c"></a>Comment : créer une boîte de dialogue (C++)

L’emplacement et la taille d’une boîte de dialogue C++, ainsi que l’emplacement et la taille des contrôles qu’elle contient, sont mesurés en unités de boîte de dialogue. Les valeurs des contrôles individuels et de la boîte de dialogue s’affichent dans le coin inférieur droit de la barre d’état de Visual Studio lorsque vous les sélectionnez.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier. RC, consultez [création d’un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Procédure

L' **éditeur de boîtes de dialogue** vous permet d’activer les éléments suivants :

### <a name="to-create-a-new-dialog-box"></a>Pour créer une boîte de dialogue

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez avec le bouton droit sur votre fichier *. RC* , puis sélectionnez **Ajouter une ressource**.

1. Dans la boîte de dialogue **Ajouter une ressource** , sélectionnez **boîte de dialogue** dans la liste **type de ressource** , puis choisissez **nouveau**.

   Si un signe plus ( **+** ) s’affiche en regard du type de ressource de **boîte** de dialogue, cela signifie que les modèles de boîte de dialogue sont disponibles. Sélectionnez le signe plus (+) pour développer la liste des modèles, sélectionnez un modèle, puis choisissez **nouveau**.

   La nouvelle boîte de dialogue s’ouvre dans l' **éditeur de boîtes de dialogue**.

Vous pouvez également ouvrir des boîtes de dialogue existantes dans l’éditeur de boîtes de dialogue pour les modifier.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Pour créer une boîte de dialogue qu’un utilisateur ne peut pas quitter

Vous pouvez créer une boîte de dialogue d’exécution qu’un utilisateur ne peut pas quitter. Ce type de boîte de dialogue est utile pour les ouvertures de session et pour le verrouillage d’application ou de document.

1. Dans le volet **Propriétés** de la boîte de dialogue, affectez à la propriété du **menu système** la valeur **`false`** .

   Ce paramètre désactive le menu système de la boîte de dialogue et le bouton **Fermer** .

1. Dans le formulaire de boîte de dialogue, supprimez les boutons **Annuler** et **OK** .

   Au moment de l’exécution, un utilisateur ne peut pas quitter une boîte de dialogue modale qui possède ces caractéristiques.

Pour permettre le test de ce type de boîte de dialogue, la fonction de test de la boîte de dialogue détecte quand la **touche Échap** est enfoncée. La touche **Échap** est également appelée clé virtuelle VK_ESCAPE. Quelle que soit la façon dont la boîte de dialogue est conçue pour se comporter au moment de l’exécution, vous pouvez terminer le mode test en appuyant sur **Échap**.

> [!NOTE]
> Pour les applications MFC, pour créer une boîte de dialogue que les utilisateurs ne peuvent pas quitter, vous devez remplacer le comportement par défaut de `OnOK` et, `OnCancel` car même si vous supprimez les boutons associés, la boîte de dialogue peut toujours être ignorée en appuyant sur **entrée** ou **Échap**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Pour spécifier l’emplacement et la taille d’une boîte de dialogue

Vous pouvez définir des propriétés dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour spécifier l’emplacement d’affichage d’une boîte de dialogue à l’écran.

- Propriété de **Centre** booléenne.

   Si vous définissez la valeur sur **true**, la boîte de dialogue s’affiche toujours au centre de l’écran. Si vous affectez à cette propriété la **valeur false**, vous pouvez définir les propriétés **xpos** et **YPos** .

- Les propriétés **xpos** et **YPos** utilisées pour définir explicitement l’emplacement où la boîte de dialogue s’affiche à l’écran.

   Ces propriétés de position sont des valeurs de décalage à partir de l’angle supérieur gauche de la zone d’affichage, qui est défini comme `{X=0, Y=0}` .

- Propriété d' **alignement absolu** qui affecte la position.

   Si la **valeur est true**, les coordonnées sont relatives à l’écran. Si la **valeur est false**, les coordonnées sont relatives à la fenêtre du propriétaire de la boîte de dialogue.

### <a name="to-test-a-dialog-box"></a>Pour tester une boîte de dialogue

Lorsque vous créez une boîte de dialogue, vous pouvez simuler et tester son comportement au moment de l’exécution sans compiler votre programme. Dans ce mode, vous pouvez :

- Taper du texte, effectuer des sélections dans des listes de zone de liste déroulante, activer ou désactiver des options, et choisir des commandes

- Tester l’ordre de tabulation

- Tester le groupement des contrôles tels que les cases à cocher et les cases d’option

- Tester les raccourcis clavier pour les contrôles dans la boîte de dialogue

> [!NOTE]
> Les connexions au code de boîte de dialogue effectuées à l’aide d’assistants ne sont pas incluses dans la simulation.

Quand vous testez une boîte de dialogue, elle s’affiche généralement à un emplacement qui est relatif à la fenêtre principale du programme. Si vous avez défini la propriété **Absolute align** de la boîte de dialogue sur **true**, la boîte de dialogue s’affiche à une position relative au coin supérieur gauche de l’écran.

1. Lorsque l' **éditeur de boîtes de dialogue** est la fenêtre active, accédez à menu tester le **format** de la  >  **boîte de dialogue**.

1. Pour mettre fin à la simulation, appuyez sur **Échap** ou sélectionnez le bouton **Fermer** dans la boîte de dialogue que vous testez.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)<br/>
[Comment : gérer les contrôles de boîte de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
