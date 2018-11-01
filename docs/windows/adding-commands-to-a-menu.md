---
title: Ajout de commandes à un Menu (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.menu
helpviewer_keywords:
- menu items, adding to menus
- menus [C++], adding items
- commands [C++], adding to menus
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
ms.openlocfilehash: 71a3a13b3c86fa4a4238fd9a42dd45b48ef318de
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571416"
---
# <a name="adding-commands-to-a-menu-c"></a>Ajout de commandes à un Menu (C++)

### <a name="to-add-commands-to-a-menu"></a>Pour ajouter des commandes à un menu

1. [Créer un menu](../windows/creating-a-menu.md).

2. Cliquez sur un nom de menu, par exemple, **fichier**.

   Chaque menu sera développé et exposera une zone Nouvel élément pour les commandes. Par exemple, vous pouvez ajouter les commandes **New**, **Open**, et **fermer** à un **fichier** menu.

3. Dans la zone Nouvel élément, tapez le nom de la nouvelle commande de menu.

   > [!NOTE]
   > Le texte que vous tapez s’affiche dans l’ **Éditeur de menus** et dans la zone **Légende** de la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.

   > [!TIP]
   > Vous pouvez définir une touche mnémonique (touche d'accès rapide) qui permet à l'utilisateur de sélectionner la commande de menu. Tapez une esperluette (`&`) devant une lettre pour spécifier que le mnémonique. L'utilisateur peut sélectionner la commande de menu en tapant cette lettre.

4. Dans le **propriétés** fenêtre, sélectionnez le menu de commande des propriétés qui s’appliquent. Pour plus d’informations, consultez [propriétés de commande de Menu](../windows/menu-command-properties.md).

5. Dans le **invite** zone le **propriétés** fenêtre, tapez la chaîne d’invite vous souhaitez voir apparaître dans la barre d’état de votre application.

   Cela crée une entrée dans la table de chaînes avec le même identificateur de ressource que la commande de menu que vous avez créée.

   > [!NOTE]
   > Les invites s’appliquent uniquement aux éléments de menu avec un **contextuelle** propriété du **True**. Par exemple, les éléments de menu de niveau supérieur peuvent avoir des invites s'ils ont des éléments de sous-menu. L’objectif d’un **invite** consiste à indiquer ce qui se produit si un utilisateur clique sur l’élément de menu.

6. Appuyez sur **entrée** pour terminer la commande de menu.

   La zone Nouvel élément est sélectionnée pour vous permettre de créer des commandes de menu supplémentaires.

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeur de menus](../windows/menu-editor.md)