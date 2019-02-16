---
title: Création de Menus (C++)
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
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
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
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
ms.openlocfilehash: da5fc355ae11ee5efb1c58be9e33bd4fb8bff02d
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320521"
---
# <a name="creating-menus-c"></a>Création de Menus (C++)

> [!NOTE]
> Le **des ressources, fenêtre** n’est pas disponible dans les éditions Express.

Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="create-a-standard-menu"></a>Créer un menu standard

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

## <a name="create-a-submenu"></a>Créer un sous-menu

1. Sélectionnez la commande de menu pour lequel vous souhaitez créer un sous-menu.

1. Dans la zone **Nouvel élément** qui apparaît à droite, tapez le nom de la nouvelle commande de menu. Cette nouvelle commande apparaît en premier dans le sous-menu.

1. Ajoutez des commandes de menu supplémentaires au sous-menu.

## <a name="to-insert-a-new-menu-between-existing-menus"></a>Pour insérer un nouveau menu parmi des menus existants

Sélectionnez un nom de menu d’existant et appuyez sur la **insérer** clé. Le **un nouvel élément** boîte est insérée avant l’élément sélectionné.

   \- ou -

Avec le bouton droit sur la barre de menus, choisissez **Insérer nouveau** dans le menu contextuel.

## <a name="add-commands-to-a-menu"></a>Ajouter des commandes à un menu

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

## <a name="create-pop-up-menus"></a>Créer des menus contextuels

Les[menus contextuels](../mfc/menus-mfc.md) affichent les commandes fréquemment utilisées. Ils dépendent du contexte selon l'emplacement du pointeur. L'utilisation de menus contextuels dans votre application nécessite la création du menu en question, puis sa connexion au code de l'application.

Une fois que vous avez créé la ressource de menu, votre code d’application doit charger cette ressource et utiliser [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) pour faire apparaître le menu. Une fois que l’utilisateur a fermé le menu contextuel en sélectionnant à l’extérieur ou qu’il a sélectionné une commande, cette fonction est retournée. Si l'utilisateur choisit une commande, ce message de commande est envoyé à la fenêtre dont le handle a été passé.

### <a name="to-create-a-pop-up-menu"></a>Pour créer un menu contextuel

1. [Créez un menu](../windows/creating-a-menu.md) avec un titre vide (ne fournissez pas de **légende**).

1. [Ajoutez une commande de menu au nouveau menu](../windows/adding-commands-to-a-menu.md). Déplacer vers la première commande de menu sous le titre de menu vide (la légende temporaire indique `Type Here`). Tapez une **légende** et les autres informations appropriées.

   Répétez ce processus pour les autres commandes de menu du menu contextuel.

1. Enregistrez la ressource de menu.

### <a name="to-connect-a-pop-up-menu-to-your-application"></a>Pour connecter un menu contextuel à votre application

1. Ajoutez un gestionnaire de messages pour WM_CONTEXTMENU (par exemple). Pour plus d’informations, consultez [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

1. Ajoutez le code suivant au gestionnaire de messages :

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > Le [CPoint](../atl-mfc-shared/reference/cpoint-class.md) passé par le message gestionnaire est en coordonnées d’écran.

   > [!NOTE]
   > Connexion d’un menu contextuel à votre application nécessite des MFC.

### <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>Pour afficher une ressource de menu sous forme de menu contextuel

Normalement, lorsque vous travaillez dans le **Menu** éditeur, une ressource de menu s’affiche comme une barre de menus. Toutefois, il est possible que des ressources de menu soient ajoutées à la barre de menus de l'application pendant l'exécution du programme.

Le menu contextuel et choisissez **afficher comme Popup** dans le menu contextuel.

   Cette option est uniquement une préférence d’affichage et ne peut pas modifier votre menu.

   > [!NOTE]
   > Pour revenir à la vue de la barre de menus, cliquez sur **afficher comme Popup** à nouveau (ce qui supprime la coche et retourne l’affichage de la barre de menus).

## <a name="edit-multiple-menus-or-menu-commands"></a>Modifier plusieurs menus ou commandes de menu

### <a name="to-select-multiple-menu-commands"></a>Pour sélectionner plusieurs commandes de menu

Vous pouvez sélectionner plusieurs noms de menus ou commandes de menu pour exécuter des opérations en bloc telles que la suppression ou modification des propriétés.

Tout en maintenant enfoncée la **Ctrl** enfoncée, sélectionnez les menus ou les commandes de sous-menu souhaitées.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Déplacer et copier des menus et commandes de menu

Vous pouvez déplacer ou copier des menus et des commandes de menu par glisser-déplacer ou à l'aide des commandes du menu contextuel.

#### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Pour déplacer ou copier des menus ou des commandes de menu par glisser-déplacer

1. Faites glisser ou copiez l'élément que vous souhaitez déplacer vers :

   - Un nouvel emplacement dans le menu actuel.

   - Un autre menu. (Vous pouvez naviguer vers d'autres menus en faisant glisser le pointeur de la souris au-dessus de ces derniers.)

1. Déplacez la commande de menu quand le guide d'insertion affiche la position souhaitée.

#### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Pour déplacer ou copier des menus ou des commandes de menu à l'aide des commandes de menu contextuel

1. Cliquez avec le bouton droit sur un ou plusieurs menus ou commandes de menu.

1. Dans le menu contextuel, choisissez **Couper** (pour déplacer) ou **Copier**.

1. Si vous souhaitez déplacer les éléments vers un autre menu ressource ou le fichier de script de ressources, [ouvrir dans une autre fenêtre](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

1. Sélectionnez la position du menu ou de la commande de menu où vous souhaitez effectuer le déplacement ou la copie.

1. Dans le menu contextuel, choisissez **Coller**. L'élément déplacé ou copié est placé avant l'élément sélectionné.

   > [!NOTE]
   > Vous pouvez également faire glisser, copier et coller des éléments vers d'autres menus dans d'autres fenêtres de menu.

### <a name="to-delete-a-menu-or-menu-command"></a>Pour supprimer un menu ou une commande de menu

1. Cliquez avec le bouton droit sur le nom ou la commande de menu.

1. Choisissez **Supprimer** dans le menu contextuel.

   > [!NOTE]
   > De même, vous pouvez utiliser le menu contextuel pour effectuer d'autres actions telles que Copier, Couper, Coller, Insérer nouveau, Insérer un séparateur, Modifier ID, Afficher comme Popup, Vérifier les mnémoniques, etc.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)