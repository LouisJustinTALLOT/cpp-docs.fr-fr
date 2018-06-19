---
title: Ajout de commandes à un Menu | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.menu
dev_langs:
- C++
helpviewer_keywords:
- menu items, adding to menus
- menus, adding items
- commands, adding to menus
- commands
- menu items
ms.assetid: 1523a755-0ab5-42f8-9e98-bb9881564431
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: e3564a808d39aa81ed3b45a1bc5812b285199e04
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33856317"
---
# <a name="adding-commands-to-a-menu"></a>Ajout de commandes à un menu
### <a name="to-add-commands-to-a-menu"></a>Pour ajouter des commandes à un menu  
  
1.  [Créer un menu](../windows/creating-a-menu.md).  
  
2.  Cliquez sur un nom de menu, par exemple, Fichier.  
  
     Chaque menu sera développé et exposera une zone Nouvel élément pour les commandes. Par exemple, vous pouvez ajouter les commandes Nouveau, Ouvrir et Fermer à un menu Fichier.  
  
3.  Dans la zone Nouvel élément, tapez le nom de la nouvelle commande de menu.  
  
    > [!NOTE]
    >  Le texte que vous tapez s’affiche dans l’éditeur de menus et dans le **légende** zone le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Vous pouvez modifier les propriétés du nouveau menu dans les deux emplacements.  
  
    > [!TIP]
    >  Vous pouvez définir une touche mnémonique (touche d'accès rapide) qui permet à l'utilisateur de sélectionner la commande de menu. Tapez une esperluette (&) devant une lettre pour spécifier qu'il s'agit de la touche mnémonique. L'utilisateur peut sélectionner la commande de menu en tapant cette lettre.  
  
4.  Dans la fenêtre Propriétés, sélectionnez les propriétés de commande de menu qui s'appliquent. Pour plus d’informations, consultez [propriétés de commande de Menu](../windows/menu-command-properties.md).  
  
5.  Dans le **invite** dans la fenêtre Propriétés, tapez la chaîne d’invite vous souhaitez voir apparaître dans la barre d’état de votre application.  
  
     Cela crée une entrée dans la table de chaînes avec le même identificateur de ressource que la commande de menu que vous avez créée.  
  
    > [!NOTE]
    >  Les invites s’appliquent uniquement aux éléments de menu avec un **Popup** propriété du **True**. Par exemple, les éléments de menu de niveau supérieur peuvent avoir des invites s'ils ont des éléments de sous-menu. Le but d'une invite est d'indiquer ce qui se passe si un utilisateur clique sur l'élément de menu.  
  
6.  Appuyez sur **entrée** pour terminer la commande de menu.  
  
     La zone Nouvel élément est sélectionnée pour vous permettre de créer des commandes de menu supplémentaires.  
  

  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de menus](../windows/menu-editor.md)   
