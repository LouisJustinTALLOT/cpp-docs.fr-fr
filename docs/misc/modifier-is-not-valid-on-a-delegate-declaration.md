---
title: "&#39;&lt;modificateur&gt;&#39; n’est pas valide dans une d&#233;claration Delegate. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bc30385"
  - "vbc30385"
helpviewer_keywords: 
  - "BC30385"
ms.assetid: cacbcdc7-dca9-4a22-b3bf-7e264308c031
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;&lt;modificateur&gt;&#39; n’est pas valide dans une d&#233;claration Delegate.
Vous avez tenté d’utiliser un modificateur, comme `Shared`, dans une déclaration Delegate. Les délégués sont des objets utilisés pour appeler les méthodes d’autres objets, en définissant un constructeur auquel la spécification d’une méthode d’objet est passée. Il n’est pas correct de spécifier un modificateur dans une déclaration Delegate.  
  
 **ID d’erreur :** BC30385  
  
### Pour corriger cette erreur  
  
1.  Supprimez le modificateur.  
  
## Voir aussi  
 [Delegate Statement](../Topic/Delegate%20Statement.md)   
 [How to: Invoke a Delegate Method](../Topic/How%20to:%20Invoke%20a%20Delegate%20Method%20\(Visual%20Basic\).md)