---
title: Commandes de menu (C++)
ms.date: 02/15/2019
helpviewer_keywords:
- menu items, properties
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
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
ms.openlocfilehash: c9abf46907c473d4cf6d9e945038f70aa75bfc48
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "59026277"
---
# <a name="menu-commands-c"></a>Commandes de menu (C++)

Les informations ci-dessous sont organisées en fonction de la **Menu** propriétés qui apparaissent dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) lorsque vous sélectionnez une commande de menu. Celles-ci sont répertoriées par ordre alphabétique bien que le **propriétés** fenêtre vous permet également d’afficher ces propriétés par catégorie.

|Propriété|Description|
|--------------|-----------------|
|**Break**|Peut avoir l'une des valeurs suivantes :<br/>  - **Aucun**: Aucun arrêt. Il s'agit de la valeur par défaut.<br/>  - **Colonne**: Pour les menus statiques, cette valeur place la commande de menu sur une nouvelle ligne.<br/>      Pour les menus contextuels, cette valeur permet de placer la commande de menu dans une nouvelle colonne sans ligne de démarcation entre les colonnes.<br/>      Cette propriété affecte l'apparence du menu uniquement au moment de l'exécution, pas dans l'éditeur de menus.<br />   - **Barre**: Identique à **colonne** à l’exception, des menus contextuels, cette valeur sépare la nouvelle colonne de l’ancienne par une ligne verticale.<br/>      Cette propriété affecte l’apparence du menu uniquement au moment de l’exécution, pas dans le **éditeur de menus**.|
|**Légende**|Texte qui indique la commande de menu (nom du menu). Pour que l'une des lettres de la légende d'une commande de menu devienne une touche mnémonique, faites-la précéder d'une esperluette (&).|
|**Activé**|Si **True**, la commande de menu est initialement activée. Type : **Bool**. Par défaut : **False**.|
|**Activé**|Si la valeur est **False**, l'élément de menu est désactivé.|
|**Grisé**|Si **True**, la commande de menu est initialement grisée et inactive. Type : **Bool**. Par défaut : **False**.|
|**Help**|Aligne l'élément de menu à droite. Par défaut : **False**.<br/><br/>Par exemple, la commande de menu **? (Aide)** est toujours sur la droite dans toutes les applications Windows. Si vous affectez cette propriété à un élément de menu, celui-ci s'affiche à l'extrémité droite et à la fin du menu. S'applique aux éléments de niveau supérieur.|
|**Id**|Symbole défini dans le fichier d'en-tête. Type : **Symbole**, **entier**, ou **chaîne entre guillemets**.<br/><br/>Vous pouvez utiliser n'importe quel symbole couramment disponible dans les éditeurs, même si la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) ne fournit pas de liste déroulante pour sélectionner des éléments.|
|**Fenêtre contextuelle**|Si **True**, la commande de menu est un menu contextuel. Type : **Bool**. Par défaut : **True** pour les menus de niveau supérieur dans une barre de menus, sinon **False**.|
|**Invite**|Contient le texte qui s'affiche dans la barre d'état quand cette commande de menu est mise en surbrillance. Le texte est placé dans la table de chaînes avec le même identificateur que la commande de menu.<br/><br/>Cette propriété est disponible pour tous les types de projet, mais les fonctionnalités d'exécution sont spécifiques à MFC.|
|**Justification de droite à gauche**|Aligne à droite la commande de menu dans la barre de menus au moment de l'exécution. Type : **Bool**. Par défaut : **False**.|
|**Ordre de droite à gauche**|Permet d'afficher les commandes de menu de droite à gauche quand l'interface est localisée dans une langue qui se lit de droite à gauche, par exemple l'hébreu ou l'arabe.|
|**Séparateur**|Si **True**, la commande de menu est un séparateur. Type : **Bool**. Par défaut : **False**.|

## <a name="associate-menu-commands"></a>Associer des commandes de Menu

Bien souvent, vous souhaitez qu’une commande de menu et une combinaison de touches du clavier exécutent la même commande de programme. Les commandes identiques sont émises à l’aide de la **éditeur de menus** pour assigner le même identificateur de ressource à la commande de menu et à une entrée dans la table d’accélérateurs de votre application. Ensuite, vous modifiez la [Légende](../windows/menu-command-properties.md) de la commande de menu pour afficher le nom de la touche accélérateur.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Pour associer une commande de menu à une touche accélérateur

1. Dans le **éditeur de menus**, sélectionnez la commande de menu souhaitée.

1. Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), ajoutez le nom de la touche accélérateur à la propriété **Légende** :

   - À la suite de la légende de menu, tapez la séquence d’échappement d’une tabulation (\t) pour que toutes les touches accélérateurs du menu soient alignées à gauche.

   - Tapez le nom de la touche de modification (**Ctrl**, **Alt**, ou **MAJ**) suivie d’un signe plus (**+**) et le nom, une lettre, ou symbole de l’autre touche.

   Par exemple, pour attribuer **Ctrl**+**O** à la **Open** commande sur le **fichier** menu, vous modifiez la commande de menu  **Légende** afin qu’il ressemble au texte suivant :

   ```
   &Open...\tCtrl+O
   ```

   La commande de menu dans le **éditeur de menus** est mis à jour pour refléter la nouvelle légende que vous le tapez.

1. [Créez l’entrée de table d’accélérateurs](../windows/adding-an-entry-to-an-accelerator-table.md) dans l’éditeur d’ **accélérateurs** et attribuez-lui le même identificateur que la commande de menu. Utilisez une combinaison de touches facile à mémoriser.

Votre application MFC peut afficher un texte descriptif pour chacune des commandes de menu, qu'un utilisateur peut sélectionner. Afficher un texte descriptif en affectant une chaîne de texte à chaque commande de menu à l’aide de la **invite** propriété dans le **propriétés** fenêtre. Si vous avez une chaîne dans la [table de chaînes](../windows/string-editor.md) dont l'ID est identique à la commande, une application MFC affiche automatiquement cette ressource de chaîne dans la barre d'état de l'application en cours d'exécution quand un utilisateur pointe sur un élément de menu.

- Pour associer une commande de menu avec une barre de chaîne de texte dans les applications MFC, d’état dans le **éditeur de menus**, sélectionnez la commande de menu. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez le texte de barre d'état associé dans la zone **Invite** .

Dans un projet C++, vous pouvez affecter une clé d’accès (un mnémonique qui permet à l’utilisateur de sélectionner le menu à l’aide du clavier) à vos menus et les commandes de menu.

- Pour affecter une clé d’accès (raccourci) à une commande de menu, tapez une esperluette (`&`) devant une lettre dans le nom de menu ou le nom de commande pour spécifier cette lettre comme touche d’accès correspondant. 

   Par exemple, « & fichier » définit **Alt**+**F** comme touche de raccourci pour le **fichier** menu dans les applications écrites pour Microsoft Windows.

   L’élément de menu fournit un indice visuel signalant qu’une touche de raccourci est affectée à l’une de lettres. La lettre qui suit que le symbole & apparaît soulignée (en fonction du système d’exploitation).

> [!NOTE]
> Assurez-vous que toutes les clés d’accès dans un menu sont uniques en double-cliquant sur votre menu et en choisissant **vérifier les mnémoniques**.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)<br/>

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->