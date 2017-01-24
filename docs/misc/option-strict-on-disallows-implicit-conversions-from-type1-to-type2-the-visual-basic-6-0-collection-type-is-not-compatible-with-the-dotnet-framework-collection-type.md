---
title: "Option Strict On interdit les conversions implicites de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39;&#160;; le type de collection de Visual Basic&#160;6.0 n’est pas compatible avec le type de collection du .NET Framework | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc30753"
  - "bc30753"
helpviewer_keywords: 
  - "BC30753"
ms.assetid: 7e1bb22e-a507-483e-bfd6-f3a43e24a232
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On interdit les conversions implicites de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39;&#160;; le type de collection de Visual Basic&#160;6.0 n’est pas compatible avec le type de collection du .NET Framework
`Option Strict On` interdit les conversions implicites de '`<type1>`' en '`<type2>`' ; le type de collection de Visual Basic 6.0 n’est pas compatible avec le type de collection du [!INCLUDE[dnprdnshort](../error-messages/tool-errors/includes/dnprdnshort_md.md)].  
  
 L’objet de collection utilisé dans Visual Basic 6.0 diffère de l’objet de collection qui est utilisé dans [!INCLUDE[vs_current_long](../misc/includes/vs_current_long_md.md)].  
  
 **ID d’erreur :** BC30753  
  
### Pour corriger cette erreur  
  
-   Convertissez explicitement les objets de collection à l’aide de l’un des mots clés de conversion de type. Les mots clés [CType, fonction](../Topic/CType%20Function%20\(Visual%20Basic\).md) et [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md) lèvent une exception au moment de l’exécution si la conversion échoue. Le mot\-clé [TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md) retourne [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md) si la conversion échoue.  
  
## Voir aussi  
 [CType, fonction](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)   
 [NIB Collections en Visual Basic](http://msdn.microsoft.com/fr-fr/8b2b7845-2251-4573-8dd3-c9f9c0a66a21)