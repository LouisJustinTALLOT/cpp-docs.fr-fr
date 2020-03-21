---
title: Commandes de menuC++()
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
ms.openlocfilehash: 972478923a7c4c60d8ff949c5532b00a1de1efc0
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80075505"
---
# <a name="menu-commands-c"></a>Commandes de menuC++()

Les informations ci-dessous sont organisées en fonction des propriétés de **menu** qui s’affichent dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) lorsque vous sélectionnez une commande de menu. Elles sont répertoriées par ordre alphabétique, mais la fenêtre **Propriétés** vous permet également d’afficher ces propriétés par catégorie.

|Propriété|Description|
|--------------|-----------------|
|**Break**|Peut prendre l'une des valeurs suivantes :<br/>  - **aucun**: aucun arrêt. Il s’agit de la valeur par défaut.<br/>  - **Colonne**: pour les menus statiques, cette valeur permet de placer la commande de menu sur une nouvelle ligne.<br/>      Pour les menus contextuels, cette valeur permet de placer la commande de menu dans une nouvelle colonne sans ligne de démarcation entre les colonnes.<br/>      Cette propriété affecte l'apparence du menu uniquement au moment de l'exécution, pas dans l'éditeur de menus.<br />   **barre**de - : identique à la **colonne** , à l’exception de, pour les menus contextuels, cette valeur sépare la nouvelle colonne de l’ancienne colonne par une ligne verticale.<br/>      La définition de cette propriété affecte l’apparence du menu uniquement au moment de l’exécution, pas dans l' **éditeur de menus**.|
|**Légende**|Texte qui indique la commande de menu (nom du menu). Pour que l'une des lettres de la légende d'une commande de menu devienne une touche mnémonique, faites-la précéder d'une esperluette (&).|
|**Activé**|Si la **valeur est true**, la commande de menu est initialement activée. Type : **bool**. Valeur par défaut : **False**.|
|**Activé**|Si la valeur est **False**, l'élément de menu est désactivé.|
|**Grisé**|Si la **valeur est true**, la commande de menu est initialement grisée et inactive. Type : **bool**. Valeur par défaut : **False**.|
|**Aide**|Aligne l'élément de menu à droite. Valeur par défaut : **False**.<br/><br/>Par exemple, la commande de menu **? (Aide)** est toujours sur la droite dans toutes les applications Windows. Si vous affectez cette propriété à un élément de menu, celui-ci s'affiche à l'extrémité droite et à la fin du menu. S'applique aux éléments de niveau supérieur.|
|**Identifiant**|Symbole défini dans le fichier d'en-tête. Type : **symbole**, **entier**ou **chaîne entre guillemets**.<br/><br/>Vous pouvez utiliser n'importe quel symbole couramment disponible dans les éditeurs, même si la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) ne fournit pas de liste déroulante pour sélectionner des éléments.|
|**Popup**|Si la **valeur est true**, la commande de menu est un menu contextuel. Type : **bool**. Valeur par défaut : **true** pour les menus de niveau supérieur dans une barre de menus, sinon **false**.|
|**Prompt**|Contient le texte qui s'affiche dans la barre d'état quand cette commande de menu est mise en surbrillance. Le texte est placé dans la table de chaînes avec le même identificateur que la commande de menu.<br/><br/>Cette propriété est disponible pour tous les types de projet, mais les fonctionnalités d'exécution sont spécifiques à MFC.|
|**Justification de droite à gauche**|Aligne à droite la commande de menu dans la barre de menus au moment de l'exécution. Type : **bool**. Valeur par défaut : **False**.|
|**Ordre de droite à gauche**|Permet d'afficher les commandes de menu de droite à gauche quand l'interface est localisée dans une langue qui se lit de droite à gauche, par exemple l'hébreu ou l'arabe.|
|**Separator**|Si la **valeur est true**, la commande de menu est un séparateur. Type : **bool**. Valeur par défaut : **False**.|

## <a name="associate-menu-commands"></a>Associer des commandes de menu

Bien souvent, vous souhaitez qu’une commande de menu et une combinaison de touches du clavier exécutent la même commande de programme. Des commandes identiques sont émises à l’aide de l' **éditeur de menus** pour assigner le même identificateur de ressource à la commande de menu et à une entrée dans la table d’accélérateurs de votre application. Ensuite, vous modifiez la [Légende](../windows/menu-command-properties.md) de la commande de menu pour afficher le nom de la touche accélérateur.

### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Pour associer une commande de menu à une touche accélérateur

1. Dans l' **éditeur de menus**, sélectionnez la commande de menu souhaitée.

1. Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), ajoutez le nom de la touche accélérateur à la propriété **Légende** :

   - À la suite de la légende de menu, tapez la séquence d’échappement d’une tabulation (\t) pour que toutes les touches accélérateurs du menu soient alignées à gauche.

   - Tapez le nom de la touche de modification (**CTRL**, **ALT**ou **MAJ**) suivi d’un signe plus ( **+** ) et du nom, de la lettre ou du symbole de la touche supplémentaire.

   Par exemple, pour affecter **Ctrl**+**O** à la commande **ouvrir** du menu **fichier** , vous modifiez la **légende** de la commande de menu pour qu’elle ressemble au texte suivant :

   ```
   &Open...\tCtrl+O
   ```

   La commande de menu dans l' **éditeur de menus** est mise à jour pour refléter la nouvelle légende à mesure que vous la tapez.

1. [Créez l’entrée de table d’accélérateurs](../windows/adding-an-entry-to-an-accelerator-table.md) dans l’éditeur d’ **accélérateurs** et attribuez-lui le même identificateur que la commande de menu. Utilisez une combinaison de touches facile à mémoriser.

Votre application MFC peut afficher un texte descriptif pour chacune des commandes de menu qu’un utilisateur peut sélectionner. Affichez le texte descriptif en affectant une chaîne de texte à chaque commande de menu à l’aide de la propriété **prompt** de la fenêtre **Propriétés** . Si vous avez une chaîne dans la [table de chaînes](../windows/string-editor.md) dont l'ID est identique à la commande, une application MFC affiche automatiquement cette ressource de chaîne dans la barre d'état de l'application en cours d'exécution quand un utilisateur pointe sur un élément de menu.

- Pour associer une commande de menu à une chaîne de texte de barre d’État dans les applications MFC, dans l' **éditeur de menus**, sélectionnez la commande de menu. Dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window), tapez le texte de barre d'état associé dans la zone **Invite** .

Dans un C++ projet, vous pouvez affecter une touche d’accès (un mnémonique qui permet à l’utilisateur de sélectionner le menu à l’aide du clavier) à vos menus et commandes de menu.

- Pour affecter une touche d’accès rapide (raccourci) à une commande de menu, tapez une esperluette (`&`) devant une lettre dans le nom de menu ou le nom de commande pour spécifier cette lettre comme clé d’accès correspondante.

   Par exemple, « & fichier » définit **Alt**+**F** comme touche de raccourci pour le menu **fichier** dans les applications écrites pour Microsoft Windows.

   L’élément de menu fournit un indice visuel signalant qu’une touche de raccourci est affectée à l’une de lettres. La lettre qui suit que le symbole & apparaît soulignée (en fonction du système d’exploitation).

> [!NOTE]
> Assurez-vous que toutes les clés d’accès d’un menu sont uniques en cliquant avec le bouton droit sur le menu et en choisissant **vérifier les mnémoniques**.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)

<!--
[Strings (ATL/MFC)](../atl-mfc-shared/strings-atl-mfc.md)<br/>-->