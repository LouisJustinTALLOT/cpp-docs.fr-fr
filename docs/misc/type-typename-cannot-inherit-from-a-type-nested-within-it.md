---
title: "Type &#39;&lt;nom_type&gt;&#39; ne peut pas h&#233;riter d’un type imbriqu&#233; dans celui-ci | Microsoft Docs"
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
  - "bc30908"
  - "vbc30908"
helpviewer_keywords: 
  - "BC30908"
ms.assetid: bca164b2-a4a9-4ed4-9f71-a9a5a42f181a
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Type &#39;&lt;nom_type&gt;&#39; ne peut pas h&#233;riter d’un type imbriqu&#233; dans celui-ci
Une définition de classe ou d’interface comprend un [Inherits Statement](../Topic/Inherits%20Statement.md) qui spécifie un type imbriqué dans celui\-ci.  
  
 L’héritage doit être linéaire, et non circulaire. Un type ne peut pas hériter d’un type qui hérite de celui\-ci.  
  
 Un type ne peut pas non plus hériter d’un type qui n’est pas encore défini. L’héritage implique la possibilité de réutiliser des membres de la classe de base, qui exige à son tour que ces membres soient définis.[!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] ne peut donc pas compiler le code comme dans l’exemple suivant.  
  
```  
Public Class outerClass ' The following statement is INVALID because innerClass is not defined. Inherits innerClass Public Class innerClass Public Sub doSomething() End Sub End Class End Class  
```  
  
 **ID d’erreur :** BC30908  
  
### Pour corriger cette erreur  
  
-   Si le type héritant \(type externe de l’imbrication\) doit hériter du type interne, déplacez le type interne hors du type externe.  
  
-   Si le type interne doit être imbriqué dans le type externe, le type externe ne peut pas hériter de celui\-ci. Supprimez [Inherits Statement](../Topic/Inherits%20Statement.md).  
  
## Voir aussi  
 [NOT IN BUILD : Héritage en Visual Basic](http://msdn.microsoft.com/fr-fr/e5e6e240-ed31-4657-820c-079b7c79313c)