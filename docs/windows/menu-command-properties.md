---
title: Propriétés de commande de menu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- menu items, properties
ms.assetid: 6d308205-3c9e-42f2-ab42-45e656940e45
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 665bc76998750f32e7de03e2fdd75fcec835774c
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014524"
---
# <a name="menu-command-properties"></a>Propriétés d'une commande de menu
Les informations ci-dessous sont organisées en fonction de la **Menu** propriétés qui apparaissent dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) lorsque vous sélectionnez une commande de menu. Celles-ci sont répertoriées par ordre alphabétique bien que le **propriétés** fenêtre vous permet également d’afficher ces propriétés par catégorie.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Break**|Peut avoir l'une des valeurs suivantes :<br /><br /> -   **Aucun** (par défaut) : aucun arrêt.<br />-   **Colonne**: pour les menus statiques, cette valeur permet de placer la commande de menu sur une nouvelle ligne. Pour les menus contextuels, cette valeur permet de placer la commande de menu dans une nouvelle colonne sans ligne de démarcation entre les colonnes. Cette propriété affecte l'apparence du menu uniquement au moment de l'exécution, pas dans l'éditeur de menus.<br />-   **Barre**: identique à **colonne** à l’exception, des menus contextuels, cette valeur sépare la nouvelle colonne de l’ancienne par une ligne verticale. Cette propriété affecte l’apparence du menu uniquement au moment de l’exécution, pas dans le **Menu** éditeur.|  
|**Légende**|Texte qui indique la commande de menu (nom du menu). Pour que l'une des lettres de la légende d'une commande de menu devienne une touche mnémonique, faites-la précéder d'une esperluette (&).|  
|**Activé**|Si **True**, la commande de menu est initialement activée. Type : **Bool**. Valeur par défaut : **False**.|  
|**Activé**|Si la valeur est **False**, l'élément de menu est désactivé.|  
|**Grisé**|Si **True**, la commande de menu est initialement grisée et inactive. Type : **Bool**. Valeur par défaut : **False**.|  
|**Aide**|Aligne l'élément de menu à droite. Par exemple, la commande de menu **? (Aide)** est toujours sur la droite dans toutes les applications Windows. Si vous affectez cette propriété à un élément de menu, celui-ci s'affiche à l'extrémité droite et à la fin du menu. S'applique aux éléments de niveau supérieur. Valeur par défaut : **False**.|  
|**ID**|Symbole défini dans le fichier d'en-tête. Type : **symbole**, **entier**, ou **chaîne entre guillemets**. Vous pouvez utiliser n'importe quel symbole couramment disponible dans les éditeurs, même si la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window) ne fournit pas de liste déroulante pour sélectionner des éléments.|  
|**Fenêtre contextuelle**|Si **True**, la commande de menu est un menu contextuel. Type : **Bool**. Par défaut : **True** pour les menus de niveau supérieur dans un menu de barre ; sinon **False**.|  
|**Invite**|Contient le texte qui s'affiche dans la barre d'état quand cette commande de menu est mise en surbrillance. Le texte est placé dans la table de chaînes avec le même identificateur que la commande de menu. Cette propriété est disponible pour tous les types de projet, mais les fonctionnalités d'exécution sont spécifiques à MFC.|  
|**Justification de droite à gauche**|Aligne à droite la commande de menu dans la barre de menus au moment de l'exécution. Type : **Bool**. Valeur par défaut : **False**.|  
|**Ordre de droite à gauche**|Permet d'afficher les commandes de menu de droite à gauche quand l'interface est localisée dans une langue qui se lit de droite à gauche, par exemple l'hébreu ou l'arabe.|  
|**Separator**|Si **True**, la commande de menu est un séparateur. Type : **Bool**. Valeur par défaut : **False**.|  
  
## <a name="requirements"></a>Configuration requise  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Éditeur de menus](../windows/menu-editor.md)