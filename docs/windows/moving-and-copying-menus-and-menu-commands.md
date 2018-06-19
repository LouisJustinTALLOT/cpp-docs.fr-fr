---
title: Déplacer et copier des Menus et commandes de Menu | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- commands, copying on menus
- menu items, moving
- commands, moving on menus
- menu items, copying
ms.assetid: 1d8df535-9922-4579-a9c2-37aeac1856eb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0da935ebdce7de61d5ed6b1a816f87b7cef7ce98
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878435"
---
# <a name="moving-and-copying-menus-and-menu-commands"></a>Déplacement et copie de menus et de commandes de menu
Vous pouvez déplacer ou copier des menus et des commandes de menu par glisser-déplacer ou à l'aide des commandes du menu contextuel.  
  
### <a name="to-move-or-copy-menus-or-menu-commands-using-the-drag-and-drop-method"></a>Pour déplacer ou copier des menus ou des commandes de menu par glisser-déplacer  
  
1.  Faites glisser ou copiez l'élément que vous souhaitez déplacer vers :  
  
    -   Un nouvel emplacement dans le menu actuel.  
  
    -   Un autre menu. (Vous pouvez naviguer vers d'autres menus en faisant glisser le pointeur de la souris au-dessus de ces derniers.)  
  
2.  Déplacez la commande de menu quand le guide d'insertion affiche la position souhaitée.  
  
### <a name="to-move-or-copy-menus-or-menu-commands-using-shortcut-menu-commands"></a>Pour déplacer ou copier des menus ou des commandes de menu à l'aide des commandes de menu contextuel  
  
1.  Cliquez avec le bouton droit sur un ou plusieurs menus ou commandes de menu.  
  
2.  Dans le menu contextuel, choisissez **Couper** (pour déplacer) ou **Copier**.  
  
3.  Si vous déplacez les éléments vers une autre ressource de menu ou un autre fichier de script de ressources, vous devez l' [ouvrir dans une autre fenêtre](/visualstudio/ide/customizing-window-layouts-in-visual-studio).  
  
4.  Sélectionnez la position du menu ou de la commande de menu où vous souhaitez effectuer le déplacement ou la copie.  
  
5.  Dans le menu contextuel, choisissez **Coller**. L'élément déplacé ou copié est placé avant l'élément sélectionné.  
  
    > [!NOTE]
    >  Vous pouvez également faire glisser, copier et coller des éléments vers d'autres menus dans d'autres fenêtres de menu.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, consultez [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de menus](../windows/menu-editor.md)