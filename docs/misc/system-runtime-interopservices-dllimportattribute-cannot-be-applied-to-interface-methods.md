---
title: "&#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; aux m&#233;thodes d’interface | Microsoft Docs"
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
  - "bc31530"
  - "vbc31530"
helpviewer_keywords: 
  - "BC31530"
ms.assetid: e63f1f7d-b7df-4637-a0f4-2783479ca1af
caps.latest.revision: 6
caps.handback.revision: 6
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;System.Runtime.InteropServices.DllImportAttribute&#39; ne peut pas &#234;tre appliqu&#233; aux m&#233;thodes d’interface
Une procédure est définie à l’intérieur d’une interface, mais la définition de procédure s’applique à <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
 Le common language runtime \(CLR\) reconnaît cet attribut et sa propriété <xref:System.Runtime.InteropServices._Assembly.EntryPoint%2A> comme désignant une procédure de remplacement définie dans une bibliothèque de liens dynamiques \(DLL\) non gérée en dehors du .NET Framework. Quand le code appelle la procédure à laquelle <xref:System.Runtime.InteropServices.DllImportAttribute> est appliqué, le common language runtime appelle plutôt la procédure non gérée désignée.  
  
 Comme la définition d’une procédure à l’intérieur d’une interface n’inclut pas d’implémentation, elle ne peut pas interagir avec des plateformes non managées en dehors du .NET Framework.  
  
 **ID d’erreur :** BC31530  
  
### Pour corriger cette erreur  
  
-   Supprimez <xref:System.Runtime.InteropServices.DllImportAttribute> de la définition de cette procédure.  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.DllImportAttribute>   
 [Interface Statement](../Topic/Interface%20Statement%20\(Visual%20Basic\).md)