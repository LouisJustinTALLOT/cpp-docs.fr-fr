---
title: "L’attribut &#39;WebMethod&#39; n’aura pas d’effet sur ce membre, car sa classe conteneur n’est pas expos&#233;e comme service web | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30771"
  - "bc30771"
helpviewer_keywords: 
  - "BC30771"
ms.assetid: 20b09f6a-b61a-4d89-9ca5-4632b5e68e65
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# L’attribut &#39;WebMethod&#39; n’aura pas d’effet sur ce membre, car sa classe conteneur n’est pas expos&#233;e comme service web
L’attribut <xref:System.Web.Services.WebMethodAttribute> autorise l’appel d’une méthode à partir des clients web distants, mais uniquement quand la classe de la méthode dérive de <xref:System.Web.Services.WebService>.  
  
 **ID d’erreur :** BC30771  
  
### Pour corriger cette erreur  
  
-   Modifiez la classe à dériver de <xref:System.Web.Services.WebService>.  
  
     — ou —  
  
-   Supprimez l’attribut <xref:System.Web.Services.WebMethodAttribute> de la méthode.  
  
## Voir aussi  
 [NIB : Procédure pas à pas : création d’un service Web XML en utilisant Visual Basic ou Visual C\#](http://msdn.microsoft.com/fr-fr/295f4c3f-9540-4bd1-b1cc-3e9cb9675cc7)