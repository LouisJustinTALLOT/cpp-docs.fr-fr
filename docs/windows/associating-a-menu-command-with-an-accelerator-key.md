---
title: Association d’une commande de Menu à une touche accélérateur | Documents Microsoft
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
ms.openlocfilehash: c4f1aa4b80aec2e7c16485c08d2505695b21f4d5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33858079"
---
# <a name="associating-a-menu-command-with-an-accelerator-key"></a>Association d'une commande de menu à une touche accélérateur
Bien souvent, vous souhaitez qu’une commande de menu et une combinaison de touches du clavier exécutent la même commande de programme. Pour cela, vous utilisez l’Éditeur de menus pour assigner le même identificateur de ressource à la commande de menu et à une entrée dans la table d’accélérateurs de votre application. Ensuite, vous modifiez la [Légende](../windows/menu-command-properties.md) de la commande de menu pour afficher le nom de la touche accélérateur.  
  
### <a name="to-associate-a-menu-command-with-an-accelerator-key"></a>Pour associer une commande de menu à une touche accélérateur  
  
1.  Dans l’ **Éditeur de menus** , sélectionnez la commande de menu souhaitée.  
  
2.  Dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window), ajoutez le nom de la touche accélérateur à la propriété **Légende** :  
  
    -   À la suite de la légende de menu, tapez la séquence d’échappement d’une tabulation (\t) pour que toutes les touches accélérateurs du menu soient alignées à gauche.  
  
    -   Tapez le nom de la touche de modification (**Ctrl**, **Alt**ou **Maj**) suivi d’un signe plus (**+**) et du nom, de la lettre ou du symbole de l’autre touche.  
  
         Par exemple, pour attribuer **Ctrl+O** à la commande **Ouvrir** du menu **Fichier** , vous devez modifier la **Légende** de la commande de menu pour qu’elle ressemble à ceci :  
  
        ```  
        &Open...\tCtrl+O   
        ```  
  
         La commande de menu dans l’Éditeur de menus est mise à jour pour refléter la nouvelle légende à mesure que vous la tapez.  
  
3.  [Créez l’entrée de table d’accélérateurs](../windows/adding-an-entry-to-an-accelerator-table.md) dans l’éditeur d’ **accélérateurs** et attribuez-lui le même identificateur que la commande de menu. Utilisez une combinaison de touches facile à mémoriser.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour plus d’informations sur l’ajout manuel des fichiers de ressources aux projets managés, l’accès aux ressources, affichage de ressources statiques et l’assignation de chaînes de ressources aux propriétés, consultez [création de fichiers de ressources pour les applications de bureau](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Pour plus d’informations sur la globalisation et localisation des ressources dans les applications managées, consultez [globalisation et localisation d’Applications .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Ajout de commandes à un Menu](../windows/adding-commands-to-a-menu.md)   
 [Éditeur de menus](../windows/menu-editor.md)