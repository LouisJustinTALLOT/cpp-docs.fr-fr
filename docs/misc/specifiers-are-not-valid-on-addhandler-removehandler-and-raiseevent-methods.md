---
title: "Les sp&#233;cificateurs ne sont pas valides pour les m&#233;thodes &#39;AddHandler&#39;, &#39;RemoveHandler&#39; et &#39;RaiseEvent&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31135"
  - "bc31135"
helpviewer_keywords: 
  - "BC31135"
ms.assetid: 2eaf5a6f-d201-4f9b-bcdf-12170cb44791
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les sp&#233;cificateurs ne sont pas valides pour les m&#233;thodes &#39;AddHandler&#39;, &#39;RemoveHandler&#39; et &#39;RaiseEvent&#39;
Les déclarations de méthode `AddHandler`, `RemoveHandler` et `RaiseEvent` ne peuvent pas être modifiées avec des mots clés tels que `Public` ou `ReadOnly`. Seules les déclarations modifiables peuvent contenir de tels mots clés.  
  
 **ID d’erreur :** BC31135  
  
### Pour corriger cette erreur  
  
-   Supprimez le mot clé de la déclaration de méthode.  
  
## Voir aussi  
 [Event Statement](../Topic/Event%20Statement.md)   
 [AddHandler \- delete](http://msdn.microsoft.com/fr-fr/fc464cf8-582c-48a6-a9c2-185c4c3d5ff8)   
 [RemoveHandler \- delete](http://msdn.microsoft.com/fr-fr/35c17f61-6e22-4b87-b6e1-3ed0c27a88a0)   
 [RaiseEvent \- delete](http://msdn.microsoft.com/fr-fr/7f765da0-5491-40b6-9ed5-24c98f9daad9)   
 [NIB Mots clés \(Visual Basic\)](http://msdn.microsoft.com/fr-fr/3a6fda51-6ade-4862-a407-1c305c3906ec)   
 [Events](../Topic/Events%20\(Visual%20Basic\).md)