---
title: Création d’un Menu (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: 438480032f1fe9208e406b4ee499267e42148a48
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702802"
---
# <a name="creating-a-menu-c"></a>Création d’un Menu (C++)

> [!NOTE]
> Le **des ressources, fenêtre** n’est pas disponible dans les éditions Express.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="to-create-a-standard-menu"></a>Pour créer un menu standard

1. À partir de la **vue** menu, sélectionnez **affichage des ressources** et ensuite avec le bouton droit sur le **Menu** du titre et choisissez **ajouter une ressource**. Choisissez **Menu**.

1. Sélectionnez la zone **Nouvel élément** (le rectangle qui contient « Tapez ici ») dans la barre de menus.

   ![Zone de nouvel élément dans l’éditeur de menus](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Zone Nouvel élément

1. Tapez un nom pour votre nouveau menu, par exemple, « Fichier ».

   Le texte que vous tapez s’affiche dans l’ **Éditeur de menus** et dans la zone **Légende** de la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   Une fois que vous avez donné un nom à votre nouveau menu dans la barre de menus, la zone Nouvel élément se déplace vers la droite (pour vous permettre d’ajouter un autre menu) et une autre zone Nouvel élément s’ouvre sous votre premier menu pour que vous puissiez y ajouter des commandes de menu.

   ![Zone nouvel élément développée](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Zone Nouvel élément avec déplacement du focus quand vous avez tapé le nom du menu

   > [!NOTE]
   > Pour créer un seul élément de menu sur la barre de menus, définissez le **contextuelle** propriété **False**.

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Pour insérer un nouveau menu parmi des menus existants

Sélectionnez un nom de menu d’existant et appuyez sur la **insérer** clé. Le **un nouvel élément** boîte est insérée avant l’élément sélectionné.

   \- ou -

Avec le bouton droit sur la barre de menus, choisissez **Insérer nouveau** dans le menu contextuel.

## <a name="to-add-commands-to-a-menu"></a>Pour ajouter des commandes à un menu

1. Créer un menu.

1. Sélectionnez un nom de menu, par exemple, **fichier**.

   Chaque menu sera développé et exposera une zone Nouvel élément pour les commandes. Par exemple, vous pouvez ajouter les commandes **New**, **Open**, et **fermer** à un **fichier** menu.

1. Dans la zone Nouvel élément, tapez le nom de la nouvelle commande de menu.

   > [!NOTE]
   > Le texte que vous tapez s’affiche dans l’ **Éditeur de menus** et dans la zone **Légende** de la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   > [!TIP]
   > Vous pouvez définir une touche mnémonique (touche d'accès rapide) qui permet à l'utilisateur de sélectionner la commande de menu. Tapez une esperluette (`&`) devant une lettre pour spécifier que le mnémonique. L'utilisateur peut sélectionner la commande de menu en tapant cette lettre.

1. Dans le **propriétés** fenêtre, sélectionnez le menu de commande des propriétés qui s’appliquent. Pour plus d’informations, consultez [propriétés de commande de Menu](../windows/menu-command-properties.md).

1. Dans le **invite** zone le **propriétés** fenêtre, tapez la chaîne d’invite vous souhaitez voir apparaître dans la barre d’état de votre application.

   Cette étape crée une entrée dans la table de chaînes avec le même identificateur de ressource que la commande de menu que vous avez créé.

   > [!NOTE]
   > Les invites s’appliquent uniquement aux éléments de menu avec un **contextuelle** propriété du **True**. Par exemple, les éléments de menu de niveau supérieur peuvent avoir des invites s'ils ont des éléments de sous-menu. L’objectif d’un **invite** consiste à indiquer ce qui se produira si l’utilisateur sélectionne l’élément de menu.

1. Appuyez sur **entrée** pour terminer la commande de menu.

   La zone Nouvel élément est sélectionnée pour vous permettre de créer des commandes de menu supplémentaires.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)