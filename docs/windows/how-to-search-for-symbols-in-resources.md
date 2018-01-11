---
title: "Comment : rechercher des symboles dans les ressources | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- symbols, finding
- resources [Visual Studio], searching for symbols
ms.assetid: 6efef8e8-d0d4-4c49-b895-314974e7791a
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 154c7a7284272ceef7a3e2d82fcd90d05069b7fe
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-search-for-symbols-in-resources"></a>Comment : rechercher des symboles dans les ressources
### <a name="to-find-symbols-in-resources"></a>Pour rechercher des symboles dans les ressources  
  
1.  À partir de la **modifier** menu, choisissez **rechercher un symbole**.  
  
2.  Dans le [boîte de dialogue Rechercher un symbole](http://msdn.microsoft.com/en-us/63e93d9c-784f-418d-a76a-723da5ff5d96), dans le **rechercher** zone, sélectionnez une chaîne de recherche antérieure dans la liste déroulante ou tapez la touche accélérateur à rechercher (par exemple, ID_ACCEL1).  
  
    > [!TIP]
    >  À utiliser [des expressions régulières](/visualstudio/ide/using-regular-expressions-in-visual-studio) pour votre recherche, vous devez utiliser le [rechercher dans les fichiers, commande](/visualstudio/ide/reference/find-command) à partir de la **modifier** menu au lieu du **rechercher un symbole**commande. Pour activer les expressions régulières, vous devez disposer du **utilisation : des Expressions régulières** case à cocher activée dans le [boîte de dialogue Rechercher](http://msdn.microsoft.com/en-us/dad03582-4931-4893-83ba-84b37f5b1600). Vous pouvez cliquer sur le bouton de flèche droite à droite de la **rechercher** à cocher pour afficher une liste d’expressions régulières de recherche. Lorsque vous sélectionnez une expression dans cette liste, elle se substitue au texte de recherche dans les **rechercher** boîte.  
  
3.  Sélectionnez un de le **trouver** options.  
  
4.  Cliquez sur **suivant**.  
  
    > [!NOTE]
    >  Vous ne pouvez pas rechercher de symboles dans les ressources de type chaîne, accélérateur ou binaire.  
  
 Pour plus d’informations sur l’ajout de ressources aux projets managés, consultez [ressources dans les applications de bureau](/dotnet/framework/resources/index) dans le *Guide du développeur .NET Framework.* Pour obtenir des informations sur l’ajout de fichiers de ressources aux projets managés, l’accès aux ressources, l’affichage de ressources statiques et l’assignation de chaînes de ressources à des propriétés, consultez [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Spécifications**  
  
 Win32  
  
## <a name="see-also"></a>Voir aussi  
 [Symboles : Identificateurs de ressources](../windows/symbols-resource-identifiers.md)   
 [Fichiers de ressources](../windows/resource-files-visual-studio.md)   
 [Éditeurs de ressources](../windows/resource-editors.md)