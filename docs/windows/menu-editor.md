---
title: Éditeur de menus (C++)
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
ms.openlocfilehash: 09d385404edbc33883d2d2add2328b33876d23ae
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2019
ms.locfileid: "66504644"
---
# <a name="menu-editor-c"></a>Éditeur de menus (C++)

Les menus permettent d’organiser les commandes de manière logique et de les trouver plus facilement. Avec le **éditeur de menus**, vous pouvez créer et modifier des menus en travaillant directement avec une barre de menus autrement étroitement ressemble à celle de votre application terminée.

> [!TIP]
> Lors de l’utilisation du **éditeur de menus**, dans de nombreux cas, vous pouvez avec le bouton droit pour afficher un menu contextuel des commandes fréquemment utilisées. Les commandes disponibles varient selon la cible du pointeur.

## <a name="how-to"></a>Comment

Le **éditeur de menus** vous permet de :

### <a name="to-create-a-standard-menu"></a>Pour créer un menu standard

1. Accédez au menu **vue** > **affichage des ressources** et avec le bouton droit sur le **Menu** titre. Choisissez **ajouter une ressource**, puis **Menu**.

1. Sélectionnez le **un nouvel élément** boîte (le rectangle qui contient *tapez ici*) sur la barre de menus.

   ![Zone de nouvel élément dans l’éditeur de menus](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **Un nouvel élément** boîte

1. Tapez un nom pour votre nouveau menu, par exemple, *fichier*.

   Le texte que vous tapez s’affiche à la fois dans le **éditeur de menus** et dans le **légende** zone le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   Une fois que vous avez donné un nom à votre nouveau menu dans la barre de menus, la zone Nouvel élément se déplace vers la droite (pour vous permettre d’ajouter un autre menu) et une autre zone Nouvel élément s’ouvre sous votre premier menu pour que vous puissiez y ajouter des commandes de menu.

   ![Zone nouvel élément développée](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   **Un nouvel élément** décalée vers la zone avec focus après avoir tapé le nom de menu

   > [!NOTE]
   > Pour créer un seul élément de menu sur la barre de menus, définissez le **contextuelle** propriété **False**.

### <a name="to-create-a-submenu"></a>Pour créer un sous-menu

1. Sélectionnez la commande de menu pour lequel vous souhaitez créer un sous-menu.

1. Dans la zone **Nouvel élément** qui apparaît à droite, tapez le nom de la nouvelle commande de menu. Cette nouvelle commande apparaît en premier dans le sous-menu.

1. Ajoutez des commandes de menu supplémentaires au sous-menu.

### <a name="to-insert-a-new-menu-between-existing-menus"></a>Pour insérer un nouveau menu parmi des menus existants

Sélectionnez un nom de menu d’existant et appuyez sur la **insérer** de clé, ou avec le bouton droit sur la barre de menus et choisissez **Insérer nouveau**.

   Le **un nouvel élément** boîte est insérée avant l’élément sélectionné.

### <a name="to-add-commands-to-a-menu"></a>Pour ajouter des commandes à un menu

1. Créer un menu. Puis sélectionnez un nom de menu, par exemple, **fichier**.

   Chaque menu sera développé et exposera une zone Nouvel élément pour les commandes. Par exemple, vous pouvez ajouter les commandes **New**, **Open**, et **fermer** à un **fichier** menu.

1. Dans la zone Nouvel élément, tapez le nom de la nouvelle commande de menu.

   > [!NOTE]
   > Le texte que vous tapez s’affiche à la fois dans le **éditeur de menus** et dans le **légende** zone le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   > [!TIP]
   > Vous pouvez définir une touche mnémonique (touche d'accès rapide) qui permet à l'utilisateur de sélectionner la commande de menu. Tapez une esperluette (`&`) devant une lettre pour spécifier que le mnémonique. L'utilisateur peut sélectionner la commande de menu en tapant cette lettre.

1. Dans le **propriétés** fenêtre, sélectionnez le menu de commande des propriétés qui s’appliquent. Pour plus d’informations, consultez [propriétés de commande de Menu](../windows/menu-command-properties.md).

1. Dans le **invite** zone le **propriétés** fenêtre, tapez la chaîne d’invite vous souhaitez voir apparaître dans la barre d’état de votre application.

   Cette étape crée une entrée dans la table de chaînes avec le même identificateur de ressource que la commande de menu que vous avez créé.

   > [!NOTE]
   > Les invites s’appliquent uniquement aux éléments de menu avec un **contextuelle** propriété du **True**. Par exemple, les éléments de menu de niveau supérieur peuvent avoir des invites s'ils ont des éléments de sous-menu. L’objectif d’un **invite** consiste à indiquer ce qui se produira si l’utilisateur sélectionne l’élément de menu.

1. Appuyez sur **entrée** pour terminer la commande de menu.

   La zone Nouvel élément est sélectionnée pour vous permettre de créer des commandes de menu supplémentaires.

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>Pour sélectionner plusieurs commandes de menu pour exécuter des opérations en bloc telles que la suppression ou modification des propriétés

Tout en maintenant enfoncée la **Ctrl** enfoncée, sélectionnez les menus ou les commandes de sous-menu souhaitées.

### <a name="to-move-and-copy-menus-and-menu-commands"></a>Déplacer et copier des menus et commandes de menu

- Utilisez la méthode glisser-déplacer :

   1. Faites glisser ou copiez l'élément que vous souhaitez déplacer vers :

      - Un nouvel emplacement dans le menu actuel.

      - Un autre menu. Vous pouvez naviguer vers d’autres menus en faisant glisser le pointeur de la souris au-dessus d’eux.

   1. Déplacez la commande de menu quand le guide d'insertion affiche la position souhaitée.

- Utilisez les commandes du menu contextuel :

   1. Cliquez sur un ou plusieurs menus ou commandes de menu, puis choisissez **couper** (pour déplacer) ou **copie**.

   1. Si vous souhaitez déplacer les éléments vers un autre menu ressource ou le fichier de script de ressources, [ouvrir dans une autre fenêtre](/visualstudio/ide/customizing-window-layouts-in-visual-studio).

   1. Sélectionnez la position du menu ou de la commande de menu où vous souhaitez effectuer le déplacement ou la copie.

   1. Dans le menu contextuel, choisissez **Coller**. L'élément déplacé ou copié est placé avant l'élément sélectionné.

> [!NOTE]
> Vous pouvez également faire glisser, copier et coller des éléments vers d'autres menus dans d'autres fenêtres de menu.

### <a name="to-delete-a-menu-or-menu-command"></a>Pour supprimer un menu ou une commande de menu

Avec le bouton droit de la commande ou le nom de menu et choisissez **supprimer**.

> [!NOTE]
> De même, vous pouvez utiliser le menu contextuel pour effectuer d'autres actions telles que Copier, Couper, Coller, Insérer nouveau, Insérer un séparateur, Modifier ID, Afficher comme Popup, Vérifier les mnémoniques, etc.

## <a name="pop-up-menus"></a>Menus contextuels

Les[menus contextuels](../mfc/menus-mfc.md) affichent les commandes fréquemment utilisées. Ils dépendent du contexte selon l'emplacement du pointeur. L'utilisation de menus contextuels dans votre application nécessite la création du menu en question, puis sa connexion au code de l'application.

Une fois que vous avez créé la ressource de menu, votre code d’application doit charger cette ressource et utiliser [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu) pour faire apparaître le menu. Une fois que l’utilisateur a fermé le menu contextuel en sélectionnant à l’extérieur ou qu’il a sélectionné une commande, cette fonction est retournée. Si l'utilisateur choisit une commande, ce message de commande est envoyé à la fenêtre dont le handle a été passé.

> [!NOTE]
> Pour les programmes de bibliothèque Microsoft Foundation classes (MFC) et ATL, utilisez **Assistants Code** pour raccorder des commandes de menu au code. Pour plus d’informations, consultez [Ajout d’un événement](../ide/adding-an-event-visual-cpp.md) et [mappage des Messages à des fonctions](../mfc/reference/mapping-messages-to-functions.md).

- Pour créer un menu contextuel, créer un menu avec un titre vide et ne fournissent pas un *légende*. Ensuite, ajoutez une commande de menu au nouveau menu, déplacer vers la première commande de menu sous le titre de menu vide avec la légende temporaire *tapez ici* et tapez un *légende* et toute autre information.

   Répétez ce processus pour toutes les autres commandes de menu dans le menu contextuel et veillez à enregistrer la ressource de menu.

- Pour vous connecter à un menu contextuel à votre application, par exemple, ajoutez un gestionnaire de messages pour WM_CONTEXTMENU, puis ajoutez le code suivant au Gestionnaire de messages :

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > Le [CPoint](../atl-mfc-shared/reference/cpoint-class.md) passé par le message gestionnaire est en coordonnées d’écran.

Normalement, lorsque vous travaillez dans le **éditeur de menus**, une ressource de menu s’affiche comme une barre de menus. Toutefois, il est possible que des ressources de menu soient ajoutées à la barre de menus de l'application pendant l'exécution du programme.

- Pour afficher une ressource de menu sous forme de menu contextuel, le menu contextuel et choisissez **afficher comme Popup**.

   Cette option est uniquement une préférence d’affichage et ne peut pas modifier votre menu.

> [!TIP]
> Pour revenir à la vue de la barre de menus, sélectionnez **afficher comme Popup** à nouveau. Cette action supprime la coche et retourne l’affichage de la barre de menus.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Commandes de menu](../windows/menu-command-properties.md)<br/>
[Objets d’interface utilisateur et ID de commande](../mfc/user-interface-objects-and-command-ids.md)<br/>
[Menus](../mfc/menus-mfc.md)<br/>
[Menus](/windows/desktop/menurc/menus)