---
title: Conception d’une boîte de dialogue (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- Test Dialog command
- testing, dialog boxes
- dialog boxes [C++], testing
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 45034ee9-c554-4f4b-8c46-6ddefdee8951
ms.openlocfilehash: 4a879f6bb1cdcd4b4897e510fb21d04500dfd3f2
ms.sourcegitcommit: 52c05e10b503e834c443ef11e7ca1987e332f876
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/05/2019
ms.locfileid: "55742685"
---
# <a name="designing-a-dialog-box-c"></a>Conception d’une boîte de dialogue (C++)

L’emplacement et la taille d’une boîte de dialogue C++ et que l’emplacement et la taille des contrôles qu’il contient, sont mesurés en unités de boîte de dialogue. Les valeurs pour les contrôles individuels et de la boîte de dialogue s’affichent dans le coin inférieur droit de l’état de Visual Studio barre lorsque vous les sélectionnez.

Lorsque vous créez une boîte de dialogue, vous pouvez également simuler et tester son comportement au moment de l’exécution sans compiler votre programme. Dans ce mode, vous pouvez :

- Taper du texte, effectuer des sélections dans des listes de zone de liste déroulante, activer ou désactiver des options, et choisir des commandes

- Tester l’ordre de tabulation

- Tester le groupement des contrôles tels que les cases à cocher et les cases d’option

- Tester les raccourcis clavier pour les contrôles dans la boîte de dialogue

   > [!NOTE]
   > Les connexions au code de boîte de dialogue effectuées à l’aide des Assistants ne sont pas incluses dans la simulation.

Quand vous testez une boîte de dialogue, elle s’affiche généralement à un emplacement qui est relatif à la fenêtre principale du programme. Si vous avez défini la boîte de dialogue **Absolute Align** propriété **True**, la boîte de dialogue affiche à une position qui est relative à l’angle supérieur gauche de l’écran.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index).

## <a name="to-specify-the-location-and-size-of-a-dialog-box"></a>Pour spécifier l’emplacement et la taille d’une boîte de dialogue

Il existe trois propriétés que vous pouvez définir dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour spécifier où une boîte de dialogue s’affiche à l’écran. Le **Center** propriété est la valeur booléenne ; si vous définissez la valeur sur **True**, la boîte de dialogue s’affiche toujours dans le centre de l’écran. Si vous le définissez sur **False**, vous pouvez ensuite définir le **XPos** et **YPos** propriétés à définir explicitement l’emplacement à l’écran la boîte de dialogue s’affiche. Les propriétés de position sont des valeurs de décalage à partir de l’angle supérieur gauche de la zone d’affichage, qui est définie comme `{X=0, Y=0}`. La position est également basée sur le **Absolute Align** propriété : si **True**, les coordonnées sont exprimées par rapport à l’écran ; si **False**, les coordonnées sont exprimées par rapport à la boîte de dialogue fenêtre propriétaire.

## <a name="to-test-a-dialog-box"></a>Pour tester une boîte de dialogue

1. Lorsque le **boîte de dialogue** éditeur est la fenêtre active, dans la barre de menus, choisissez **Format** > **boîte de dialogue Test**.

1. Pour arrêter la simulation, appuyez sur **ÉCHAP**, ou sélectionnez simplement le **fermer** bouton dans la boîte de dialogue que vous testez.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Contrôles dans les boîtes de dialogue](../windows/controls-in-dialog-boxes.md)<br/>
[Éditeur de boîtes de dialogue](../windows/dialog-editor.md)<br/>
[Affichage ou masquage de la barre d’outils Éditeur de boîtes de dialogue](../windows/showing-or-hiding-the-dialog-editor-toolbar.md)