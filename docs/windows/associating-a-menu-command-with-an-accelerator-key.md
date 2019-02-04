---
title: Associer des commandes de Menu (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- keyboard shortcuts [C++], menu association
- commands [C++], associating menu commands with accelerator keys
- menu commands [C++], associating with keyboard shortcuts
- status bars [C++], associating menu items
- menus [C++], status bar text
- access keys [C++], checking
- menus [C++], shortcut keys
- keyboard shortcuts [C++], command assignments
- access keys [C++], assigning
- mnemonics [C++], adding to menus
- keyboard shortcuts [C++], uniqueness checking
- mnemonics [C++], uniqueness checking
- Check Mnemonics command
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
ms.openlocfilehash: f72fe5de3ef29b9575ef1a3138d4d114d7470fee
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55703036"
---
# <a name="associating-menu-commands-c"></a>Associer des commandes de Menu (C++)

Bien souvent, vous souhaitez qu’une commande de menu et une combinaison de touches du clavier exécutent la même commande de programme. Les commandes identiques sont émises à l’aide de la **Menu** éditeur pour assigner le même identificateur de ressource à la commande de menu et à une entrée dans la table d’accélérateurs de votre application. Ensuite, vous modifiez la [Légende](../windows/menu-command-properties.md) de la commande de menu pour afficher le nom de la touche accélérateur.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Pour associer une commande de menu à une touche accélérateur

1. Dans l’ **Éditeur de menus** , sélectionnez la commande de menu souhaitée.

1. Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), ajoutez le nom de la touche accélérateur à la propriété **Légende** :

   - À la suite de la légende de menu, tapez la séquence d’échappement d’une tabulation (\t) pour que toutes les touches accélérateurs du menu soient alignées à gauche.

   - Tapez le nom de la touche de modification (**Ctrl**, **Alt**, ou **MAJ**) suivie d’un signe plus (**+**) et le nom, une lettre, ou symbole de l’autre touche.

       Par exemple, pour attribuer **Ctrl**+**O** à la **Open** commande sur le **fichier** menu, vous modifiez la commande de menu  **Légende** afin qu’il ressemble au texte suivant :

        ```
        &Open...\tCtrl+O
        ```

       La commande de menu dans le **Menu** éditeur est mis à jour pour refléter la nouvelle légende que vous le tapez.

1. [Créez l’entrée de table d’accélérateurs](../windows/adding-an-entry-to-an-accelerator-table.md) dans l’éditeur d’ **accélérateurs** et attribuez-lui le même identificateur que la commande de menu. Utilisez une combinaison de touches facile à mémoriser.

## <a name="to-associate-a-menu-command-with-a-status-bar-text-string-in-mfc-applications"></a>Pour associer une commande de menu avec l’état de la barre chaîne de texte dans les applications MFC

Votre application MFC peut afficher un texte descriptif pour chacune des commandes de menu, qu'un utilisateur peut sélectionner. Afficher un texte descriptif en affectant une chaîne de texte à chaque commande de menu à l’aide de la **invite** propriété dans le **propriétés** fenêtre. Si vous avez une chaîne dans la [table de chaînes](../windows/string-editor.md) dont l'ID est identique à la commande, une application MFC affiche automatiquement cette ressource de chaîne dans la barre d'état de l'application en cours d'exécution quand un utilisateur pointe sur un élément de menu.

1. Dans l' **éditeur de menus** , sélectionnez la commande de menu.

1. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez le texte de barre d'état associé dans la zone **Invite** .

> [!NOTE]
> Cet ensemble d’étapes nécessite des MFC.

## <a name="to-assign-an-access-shortcut-key-to-a-menu-command"></a>Pour affecter une touche d’accès (raccourci) à une commande de menu

Dans un projet C++, vous pouvez affecter une clé d’accès (un mnémonique qui permet à l’utilisateur de sélectionner le menu à l’aide du clavier) à vos menus et les commandes de menu.

Tapez une esperluette (`&`) devant une lettre dans le nom de menu ou le nom de commande pour spécifier cette lettre comme touche d’accès correspondant. Par exemple, « & fichier » définit **Alt**+**F** comme touche de raccourci pour le **fichier** menu dans les applications écrites pour Microsoft Windows.

   L’élément de menu fournit un indice visuel signalant qu’une touche de raccourci est affectée à l’une de lettres. La lettre qui suit que le symbole & apparaît soulignée (en fonction du système d’exploitation).

   > [!NOTE]
   > Assurez-vous que toutes les touches d’accès rapide d’un menu sont uniques en cliquant avec le bouton droit sur le menu et en choisissant **Vérifier les mnémoniques** dans le menu contextuel.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)<br/>
[Ajout de commandes à un menu](../windows/adding-commands-to-a-menu.md)<br/>
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>
