---
title: Association d’une commande de Menu à une touche accélérateur | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- keyboard shortcuts, menu association
- commands, associating menu commands with accelerator keys
- menu commands, associating with keyboard shortcuts
ms.assetid: ad2de43f-b20a-4c9f-bda8-0420179da48c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8e4b1665e54a03bf7d5f4705aaa3d76962ed16a0
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2018
ms.locfileid: "39649970"
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>Association d'une commande de menu à une touche accélérateur
Bien souvent, vous souhaitez qu’une commande de menu et une combinaison de touches du clavier exécutent la même commande de programme. Pour cela, vous devez utiliser le **Menu** éditeur pour assigner le même identificateur de ressource à la commande de menu et à une entrée dans la table d’accélérateurs de votre application. Ensuite, vous modifiez la [Légende](../windows/menu-command-properties.md) de la commande de menu pour afficher le nom de la touche accélérateur.  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Pour associer une commande de menu à une touche accélérateur  
  
1.  Dans l’ **Éditeur de menus** , sélectionnez la commande de menu souhaitée.  
  
2.  Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), ajoutez le nom de la touche accélérateur à la propriété **Légende** :  
  
    -   À la suite de la légende de menu, tapez la séquence d’échappement d’une tabulation (\t) pour que toutes les touches accélérateurs du menu soient alignées à gauche.  
  
    -   Tapez le nom de la touche de modification (**Ctrl**, **Alt**, ou **MAJ**) suivie d’un signe plus (**+**) et le nom, une lettre, ou symbole de l’autre touche.  
  
         Par exemple, pour attribuer **Ctrl**+**O** à la **Open** commande sur le **fichier** menu, vous modifiez la commande de menu  **Légende** afin qu’il ressemble à ceci :  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         La commande de menu dans le **Menu** éditeur est mis à jour pour refléter la nouvelle légende que vous le tapez.  
  
3.  [Créez l’entrée de table d’accélérateurs](../windows/adding-an-entry-to-an-accelerator-table.md) dans l’éditeur d’ **accélérateurs** et attribuez-lui le même identificateur que la commande de menu. Utilisez une combinaison de touches facile à mémoriser.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [Resources in Desktop Apps](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework*. Pour plus d’informations sur l’ajout manuel de fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création des fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation de ressources dans les applications gérées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de commandes à un Menu](../windows/adding-commands-to-a-menu.md)   
 [Éditeur de menus](../windows/menu-editor.md)