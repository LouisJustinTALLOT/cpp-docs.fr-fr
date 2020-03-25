---
title: Éditeur de menusC++()
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
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
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: 3671dbe33b2d6e373e2df3d54267c6aac5bbf20d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214446"
---
# <a name="menu-editor-c"></a>Éditeur de menusC++()

Les menus permettent d’organiser les commandes de manière logique et de les trouver plus facilement. Avec l' **éditeur de menus**, vous pouvez créer et modifier des menus en travaillant directement avec une barre de menus qui ressemble étroitement à celle de votre application terminée.

> [!TIP]
> Lorsque vous utilisez l' **éditeur de menus**, dans de nombreux cas, vous pouvez cliquer avec le bouton droit pour afficher un menu contextuel des commandes fréquemment utilisées. Les commandes disponibles varient selon la cible du pointeur.

## <a name="how-to"></a>Procédure

L' **éditeur de menus** vous permet d’activer les éléments suivants :

### <a name="to-create-a-standard-menu"></a>Pour créer un menu standard

1. Accédez à la **vue** de menu > **autres > Windows** **affichage des ressources** et cliquez avec le bouton droit sur l’en-tête du **menu** . Sélectionnez **Ajouter une ressource**, puis **menu**.

1. Sélectionnez la zone **nouvel élément** (le rectangle qui contient le *type ici*) dans la barre de menus.

   ![Zone nouvel élément de l’éditeur de menus](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   Zone **nouvel élément**

1. Tapez un nom pour votre nouveau menu, par exemple *fichier*.

   Le texte que vous tapez s’affiche à la fois dans l' **éditeur de menus** et dans la zone **légende** de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   Une fois que vous avez donné un nom à votre nouveau menu dans la barre de menus, la zone Nouvel élément se déplace vers la droite (pour vous permettre d’ajouter un autre menu) et une autre zone Nouvel élément s’ouvre sous votre premier menu pour que vous puissiez y ajouter des commandes de menu.

   ![Zone de nouvel élément développée](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   Zone **nouvel élément** avec le focus déplacé après que vous avez tapé le nom du menu

   > [!NOTE]
   > Pour créer un menu à un seul élément dans la barre de menus, affectez la valeur **false**à la propriété **Popup** .

### <a name="to-create-a-submenu"></a>Pour créer un sous-menu

1. Sélectionnez la commande de menu pour laquelle vous souhaitez créer un sous-menu.

1. Dans la zone **Nouvel élément** qui apparaît à droite, tapez le nom de la nouvelle commande de menu. Cette nouvelle commande apparaît en premier dans le sous-menu.

1. Ajoutez des commandes de menu supplémentaires au sous-menu.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>Pour insérer un nouveau menu parmi des menus existants

Sélectionnez un nom de menu existant et appuyez sur la touche **Inser** , ou cliquez avec le bouton droit sur la barre de menus et choisissez **Insérer nouveau**.

   La zone **nouvel élément** est insérée avant l’élément sélectionné.

### <a name="to-add-commands-to-a-menu"></a>Pour ajouter des commandes à un menu

1. Créez un menu. Sélectionnez ensuite un nom de menu, par exemple **fichier**.

   Chaque menu sera développé et exposera une zone Nouvel élément pour les commandes. Par exemple, vous pouvez ajouter les commandes **nouveau**, **ouvrir**et **Fermer** à un menu **fichier** .

1. Dans la zone Nouvel élément, tapez le nom de la nouvelle commande de menu.

   > [!NOTE]
   > Le texte que vous tapez s’affiche à la fois dans l' **éditeur de menus** et dans la zone **légende** de la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   > [!TIP]
   > Vous pouvez définir une touche mnémonique (touche d'accès rapide) qui permet à l'utilisateur de sélectionner la commande de menu. Tapez une esperluette (`&`) devant une lettre pour la spécifier comme mnémonique. L'utilisateur peut sélectionner la commande de menu en tapant cette lettre.

1. Dans la fenêtre **Propriétés** , sélectionnez les propriétés de commande de menu qui s’appliquent. Pour plus d’informations, consultez Propriétés de la [commande de menu](../windows/menu-command-properties.md).

1. Dans la zone **invite** de la fenêtre **Propriétés** , tapez la chaîne d’invite que vous souhaitez afficher dans la barre d’état de votre application.

   Cette étape crée une entrée dans la table de chaînes avec le même identificateur de ressource que la commande de menu que vous avez créée.

   > [!NOTE]
   > Les invites ne peuvent s’appliquer qu’aux éléments de menu dont la propriété **Popup** a la **valeur true**. Par exemple, les éléments de menu de niveau supérieur peuvent avoir des invites s'ils ont des éléments de sous-menu. L’objectif d’une **invite** est d’indiquer ce qui se produit si un utilisateur sélectionne l’élément de menu.

1. Appuyez sur **entrée** pour terminer la commande de menu.

   La zone Nouvel élément est sélectionnée pour vous permettre de créer des commandes de menu supplémentaires.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>Pour sélectionner plusieurs commandes de menu afin d’exécuter des opérations en bloc, telles que la suppression ou la modification de propriétés

Tout en maintenant la touche **CTRL** enfoncée, sélectionnez les menus ou les commandes de sous-menu souhaitées.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Pour déplacer et copier des menus et des commandes de menu

- Utilisez la méthode de glisser-déplacer :

   1. Faites glisser ou copiez l'élément que vous souhaitez déplacer vers :

      - Un nouvel emplacement dans le menu actuel.

      - Un autre menu. Vous pouvez naviguer vers d’autres menus en faisant glisser le pointeur de la souris dessus.

   1. Déplacez la commande de menu quand le guide d'insertion affiche la position souhaitée.

- Utilisez les commandes du menu contextuel :

   1. Cliquez avec le bouton droit sur un ou plusieurs menus ou commandes de menu, puis choisissez **couper** (pour déplacer) ou **copier**.

   1. Si vous déplacez les éléments vers une autre ressource de menu ou un autre fichier de script de ressources, [Ouvrez-le dans une autre fenêtre](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Sélectionnez la position du menu ou de la commande de menu où vous souhaitez effectuer le déplacement ou la copie.

   1. Dans le menu contextuel, choisissez **Coller**. L'élément déplacé ou copié est placé avant l'élément sélectionné.

> [!NOTE]
> Vous pouvez également faire glisser, copier et coller des éléments vers d'autres menus dans d'autres fenêtres de menu.

### <a name="to-delete-a-menu-or-menu-command"></a>Pour supprimer un menu ou une commande de menu

Cliquez avec le bouton droit sur le nom ou la commande du menu et choisissez **supprimer**.

> [!NOTE]
> De même, vous pouvez utiliser le menu contextuel pour effectuer d'autres actions telles que Copier, Couper, Coller, Insérer nouveau, Insérer un séparateur, Modifier ID, Afficher comme Popup, Vérifier les mnémoniques, etc.

## <a name="pop-up-menus"></a>Menus contextuels

Les[menus contextuels](../mfc/menus-mfc.md) affichent les commandes fréquemment utilisées. Ils dépendent du contexte selon l'emplacement du pointeur. L'utilisation de menus contextuels dans votre application nécessite la création du menu en question, puis sa connexion au code de l'application.

Une fois que vous avez créé la ressource de menu, votre code d’application doit charger la ressource de menu et utiliser [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu) pour faire apparaître le menu. Une fois que l’utilisateur a fermé le menu contextuel en le sélectionnant à l’extérieur ou qu’il a sélectionné une commande, cette fonction retourne. Si l'utilisateur choisit une commande, ce message de commande est envoyé à la fenêtre dont le handle a été passé.

> [!NOTE]
> Pour les programmes de bibliothèque MFC (Microsoft Foundation Class) et les programmes ATL, utilisez les **assistants code** pour raccorder des commandes de menu au code. Pour plus d’informations, consultez [Ajout d’un événement](../ide/adding-an-event-visual-cpp.md) et [mappage de messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

- Pour créer un menu contextuel, créez un menu avec un titre vide et ne fournissez pas de *légende*. Ensuite, ajoutez une commande de menu au nouveau menu, accédez à la première commande de menu sous le titre de menu vide avec le *type* de légende temporaire ici et tapez une *légende* et toute autre information.

   Répétez cette procédure pour toutes les autres commandes de menu du menu contextuel et veillez à enregistrer la ressource de menu.

- Pour connecter un menu contextuel à votre application, par exemple, ajoutez un gestionnaire de messages pour WM_CONTEXTMENU, puis ajoutez le code suivant au gestionnaire de messages :

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > Le [CPoint](../atl-mfc-shared/reference/cpoint-class.md) passé par le gestionnaire de messages est exprimé en coordonnées d’écran.

Normalement, lorsque vous travaillez dans l' **éditeur de menus**, une ressource de menu s’affiche sous la forme d’une barre de menus. Toutefois, il est possible que des ressources de menu soient ajoutées à la barre de menus de l'application pendant l'exécution du programme.

- Pour afficher une ressource de menu sous la forme d’un menu contextuel, cliquez avec le bouton droit sur le menu et choisissez **afficher comme Popup**.

   Cette option n’est qu’une préférence d’affichage et ne modifie pas votre menu.

> [!TIP]
> Pour revenir à l’affichage de la barre de menus, sélectionnez Afficher à nouveau **sous forme de fenêtre contextuelle** . Cette action supprime la coche et retourne votre affichage de la barre de menus.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Commandes de menu](../windows/menu-command-properties.md)<br/>
[Objets d’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menus](../mfc/menus-mfc.md)<br/>
[Menus](/windows/win32/menurc/menus)
