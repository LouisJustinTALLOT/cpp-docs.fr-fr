---
title: 'Procédure : Créer une boîte de dialogue (C++)'
ms.date: 02/15/2019
f1_keywords:
- vc.editors.dialog
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
ms.openlocfilehash: c5f026683881ba8e608bd00089879e0e2a7b4af2
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59036326"
---
# <a name="how-to-create-a-dialog-box-c"></a>Procédure : Créer une boîte de dialogue (C++)

L’emplacement et la taille d’une boîte de dialogue C++ et que l’emplacement et la taille des contrôles qu’il contient, sont mesurés en unités de boîte de dialogue. Les valeurs pour les contrôles individuels et de la boîte de dialogue s’affichent dans le coin inférieur droit de l’état de Visual Studio barre lorsque vous les sélectionnez.

> [!NOTE]
> Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).

## <a name="how-to"></a>Comment

Le **boîte de dialogue Éditeur** vous permet de :

### <a name="to-create-a-new-dialog-box"></a>Pour créer une nouvelle boîte de dialogue

1. Dans [affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), cliquez sur votre *.rc* fichier et sélectionnez **ajouter une ressource**.

1. Dans le **ajouter une ressource** boîte de dialogue, sélectionnez **boîte de dialogue** dans le **Type de ressource** liste, puis choisissez **New**.

   Si un signe plus (**+**) apparaît en regard du **boîte de dialogue** type de ressource, cela signifie que les modèles de boîte de dialogue sont disponibles. Sélectionnez le signe plus pour développer la liste des modèles, sélectionnez un modèle et choisissez **New**.

   La nouvelle boîte de dialogue s’ouvre dans le **boîte de dialogue Éditeur**.

Vous pouvez également ouvrir des boîtes de dialogue existantes dans l’éditeur de boîte de dialogue pour la modification.

### <a name="to-create-a-dialog-box-that-a-user-cant-exit"></a>Pour créer une boîte de dialogue qu’un utilisateur ne peut pas quitter

Vous pouvez créer une boîte de dialogue d’exécution qu’un utilisateur ne peut pas quitter. Ce type de boîte de dialogue est utile pour les ouvertures de session et pour le verrouillage d’application ou de document.

1. Dans le volet **Propriétés** de la boîte de dialogue, affectez la valeur **false** à la propriété **Menu système**.

   Ce paramètre désactive le menu système de boîte de dialogue et **fermer** bouton.

1. Dans le formulaire de boîte de dialogue, supprimez les boutons **Annuler** et **OK** .

   Au moment de l’exécution, un utilisateur ne peuvent pas quitter une boîte de dialogue modale qui possède ces caractéristiques.

Pour activer le test de ce type de boîte de dialogue, la fonction de boîte de dialogue test détecte quand **ÉCHAP** est enfoncé. **ÉCHAP** est également appelé la touche virtuelle VK_ESCAPE. Quelle que soit la façon dont la boîte de dialogue est conçue de comportement au moment de l’exécution, vous pouvez terminer le mode de test en appuyant sur **ÉCHAP**.

> [!NOTE]
> Pour les applications MFC, pour créer une boîte de dialogue que les utilisateurs ne peuvent pas quitter, vous devez substituer le comportement par défaut de `OnOK` et `OnCancel` , car même si vous supprimez les boutons associés, la boîte de dialogue peut toujours être ignorée en appuyant sur  **Entrez** ou **ÉCHAP**.

### <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Pour spécifier l’emplacement et la taille d’une boîte de dialogue

Il existe des propriétés que vous pouvez définir dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour spécifier où une boîte de dialogue s’affiche à l’écran.

- La valeur booléenne **Center** propriété.

   Si vous définissez la valeur sur **True**, la boîte de dialogue s’affiche toujours dans le centre de l’écran. Si vous définissez cette propriété sur **False**, vous pouvez ensuite définir le **XPos** et **YPos** propriétés.

- Le **XPos** et **YPos** propriétés qui sont utilisées pour définir explicitement l’emplacement à l’écran la boîte de dialogue s’affiche.

   Ces propriétés de position sont des valeurs de décalage à partir de l’angle supérieur gauche de la zone d’affichage, qui est définie comme `{X=0, Y=0}`.

- Le **Absolute Align** propriété qui affecte la position.

   Si **True**, les coordonnées sont exprimées par rapport à l’écran. Si **False**, les coordonnées sont exprimées par rapport à la fenêtre du propriétaire de la boîte de dialogue.

### <a name="to-test-a-dialog-box"></a>Pour tester une boîte de dialogue

Lorsque vous créez une boîte de dialogue, vous pouvez simuler et tester son comportement au moment de l’exécution sans compiler votre programme. Dans ce mode, vous pouvez :

- Taper du texte, effectuer des sélections dans des listes de zone de liste déroulante, activer ou désactiver des options, et choisir des commandes

- Tester l’ordre de tabulation

- Tester le groupement des contrôles tels que les cases à cocher et les cases d’option

- Tester les raccourcis clavier pour les contrôles dans la boîte de dialogue

> [!NOTE]
> Connexions au code de boîte de dialogue effectuées à l’aide des Assistants ne sont pas incluses dans la simulation.

Quand vous testez une boîte de dialogue, elle s’affiche généralement à un emplacement qui est relatif à la fenêtre principale du programme. Si vous avez défini la boîte de dialogue **Absolute Align** propriété **True**, la boîte de dialogue affiche à une position qui est relative à l’angle supérieur gauche de l’écran.

1. Lorsque le **boîte de dialogue Éditeur** est la fenêtre active, accédez au menu **Format** > **boîte de dialogue Test**.

1. Pour arrêter la simulation, appuyez sur **ÉCHAP** ou sélectionnez le **fermer** bouton dans la boîte de dialogue que vous testez.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)<br/>
[Guide pratique pour Gérer les contrôles de boîte de dialogue](../windows/controls-in-dialog-boxes.md)<br/>