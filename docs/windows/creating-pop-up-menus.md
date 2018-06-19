---
title: Création de Menus contextuels | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- context menus, Menu Editor
- pop-up menus, creating
- menus, pop-up
- menus, creating
- shortcut menus, creating
- pop-up menus, displaying
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 218ed28a8b44100beead46ab13e04ad07d86c7e5
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/08/2018
ms.locfileid: "33871495"
---
# <a name="creating-pop-up-menus"></a>Création de menus contextuels
Les[menus contextuels](../mfc/menus-mfc.md) affichent les commandes fréquemment utilisées. Ils dépendent du contexte selon l'emplacement du pointeur. L'utilisation de menus contextuels dans votre application nécessite la création du menu en question, puis sa connexion au code de l'application.  
  
 Une fois que vous avez créé la ressource de menu, votre code d’application doit charger cette ressource et utiliser [TrackPopupMenu](http://msdn.microsoft.com/library/windows/desktop/ms648002) pour faire apparaître le menu. Une fois que l'utilisateur a fermé le menu contextuel en cliquant hors de ce dernier, ou qu'il a cliqué sur une commande, cette fonction est retournée. Si l'utilisateur choisit une commande, ce message de commande est envoyé à la fenêtre dont le handle a été passé.  
  
### <a name="to-create-a-pop-up-menu"></a>Pour créer un menu contextuel  
  
1.  [Créez un menu](../windows/creating-a-menu.md) avec un titre vide (ne fournissez pas de **légende**).  
  
2.  [Ajoutez une commande de menu au nouveau menu](../windows/adding-commands-to-a-menu.md). Placez-vous sur la première commande de menu sous le titre de menu vide (la légende temporaire indique « Tapez ici »). Tapez une **légende** et les autres informations appropriées.  
  
     Répétez ce processus pour les autres commandes de menu du menu contextuel.  
  
3.  Enregistrez la ressource de menu.  
  
    > [!TIP]
    >  Pour plus d'informations sur l'affichage du menu contextuel, voir [Affichage d'un menu sous la forme d'un menu contextuel](../windows/viewing-a-menu-as-a-pop-up-menu.md).  
  

  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Connexion d’un Menu contextuel à votre Application](../windows/connecting-a-pop-up-menu-to-your-application.md)   
 [Éditeur de menus](../windows/menu-editor.md)