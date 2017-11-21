---
title: "Modification d’un symbole ou un nom de symbole (ID) | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.symbol.changing
dev_langs: C++
helpviewer_keywords:
- symbol names
- symbols, names
ms.assetid: 26541832-8dba-4177-b642-e08f94502ea7
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 300c83a256e2a60ce9f7605093a2016f2d322785
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="changing-a-symbol-or-symbol-name-id"></a>Modification d'un symbole ou d'un nom de symbole (ID)
Quand vous créez une ressource ou un objet de ressource, l'environnement de développement lui assigne un nom de symbole par défaut, par exemple, IDD_DIALOG1. Vous pouvez utiliser la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) pour modifier le nom de symbole par défaut ou modifier le nom d’un symbole déjà associé à une ressource.  
  
### <a name="to-change-a-resources-symbol-name"></a>Pour changer le nom de symbole d'une ressource  
  
1.  Dans [affichage des ressources](../windows/resource-view-window.md), sélectionnez la ressource.  
  
    > [!NOTE]
    >  Si votre projet ne contient pas déjà un fichier .rc, consultez [Création d'un fichier de script de ressources](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Dans le **propriétés** fenêtre, tapez un nouveau nom de symbole ou sélectionnez dans la liste des symboles existants de la **ID** boîte.  
  
     Si vous tapez un nouveau nom de symbole, il reçoit automatiquement une valeur.  
  
 Vous pouvez utiliser la [boîte de dialogue Symboles des ressources](../windows/resource-symbols-dialog-box.md) pour modifier les noms de symboles pas actuellement assignés à une ressource. Pour plus d’informations, consultez [la modification des symboles non assignés](../windows/changing-unassigned-symbols.md).  
  

  
 Spécifications  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Restrictions relatives au nom de symbole](../windows/symbol-name-restrictions.md)   
 [ID de symbole prédéfinis](../windows/predefined-symbol-ids.md)