---
title: Modification de plusieurs Menus ou commandes de Menu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: b6f17897-2a40-4afd-97d4-a38b7661680b
ms.openlocfilehash: 45e2c4e97dc850b4d6fb13a5526911e4bd5caec2
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703218"
---
# <a name="editing-multiple-menus-or-menu-commands"></a>Modification de plusieurs Menus ou commandes de Menu

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-select-multiple-menu-commands"></a>Pour sélectionner plusieurs commandes de menu

Vous pouvez sélectionner plusieurs noms de menus ou commandes de menu pour exécuter des opérations en bloc telles que la suppression ou modification des propriétés.

Tout en maintenant enfoncée la **Ctrl** enfoncée, sélectionnez les menus ou les commandes de sous-menu souhaitées.

## <a name="to-move-and-copy-menus-and-menu-commands"></a>Déplacer et copier des menus et commandes de menu

Vous pouvez déplacer ou copier des menus et des commandes de menu par glisser-déplacer ou à l'aide des commandes du menu contextuel.

### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Pour déplacer ou copier des menus ou des commandes de menu par glisser-déplacer

1. Faites glisser ou copiez l'élément que vous souhaitez déplacer vers :

   - Un nouvel emplacement dans le menu actuel.

   - Un autre menu. (Vous pouvez naviguer vers d'autres menus en faisant glisser le pointeur de la souris au-dessus de ces derniers.)

1. Déplacez la commande de menu quand le guide d'insertion affiche la position souhaitée.

### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Pour déplacer ou copier des menus ou des commandes de menu à l'aide des commandes de menu contextuel

1. Cliquez avec le bouton droit sur un ou plusieurs menus ou commandes de menu.

1. Dans le menu contextuel, choisissez **Couper** (pour déplacer) ou **Copier**.

1. Si vous souhaitez déplacer les éléments vers un autre menu ressource ou le fichier de script de ressources, [ouvrir dans une autre fenêtre](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Sélectionnez la position du menu ou de la commande de menu où vous souhaitez effectuer le déplacement ou la copie.

1. Dans le menu contextuel, choisissez **Coller**. L'élément déplacé ou copié est placé avant l'élément sélectionné.

   > [!NOTE]
   > Vous pouvez également faire glisser, copier et coller des éléments vers d'autres menus dans d'autres fenêtres de menu.

## <a name="to-delete-a-menu-or-menu-command"></a>Pour supprimer un menu ou une commande de menu

1. Cliquez avec le bouton droit sur le nom ou la commande de menu.

1. Choisissez **Supprimer** dans le menu contextuel.

   > [!NOTE]
   > De même, vous pouvez utiliser le menu contextuel pour effectuer d'autres actions telles que Copier, Couper, Coller, Insérer nouveau, Insérer un séparateur, Modifier ID, Afficher comme Popup, Vérifier les mnémoniques, etc.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)