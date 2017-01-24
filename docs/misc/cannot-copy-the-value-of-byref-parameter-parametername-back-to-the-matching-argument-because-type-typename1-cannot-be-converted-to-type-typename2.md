---
title: "Impossible de recopier la valeur du param&#232;tre &#39;ByRef&#39; &#39;&lt;nom_param&#232;tre&gt;&#39; dans l’argument correspondant, car le type &#39;&lt;nom_type1&gt;&#39; ne peut pas &#234;tre converti en type &#39;&lt;nom_type2&gt;&#39; | Microsoft Docs"
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
  - "vbc33037"
  - "BC33037"
helpviewer_keywords: 
  - "BC33037"
ms.assetid: 3ff137e2-e062-4e54-abf5-e902e2d18968
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Impossible de recopier la valeur du param&#232;tre &#39;ByRef&#39; &#39;&lt;nom_param&#232;tre&gt;&#39; dans l’argument correspondant, car le type &#39;&lt;nom_type1&gt;&#39; ne peut pas &#234;tre converti en type &#39;&lt;nom_type2&gt;&#39;
Une procédure est déclarée avec un type de paramètre qui ne peut pas être reconverti en type d’argument appelant.  
  
 Quand vous définissez une classe ou une structure, vous pouvez définir un ou plusieurs opérateurs de conversion pour convertir le type de la classe ou de la structure en d’autres types. Vous pouvez également définir des opérateurs de conversion inverse pour convertir ces autres types vers le type de votre classe ou de votre structure. Quand vous utilisez votre type de classe ou de structure dans un appel de procédure, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] peut utiliser ces opérateurs de conversion pour convertir le type d’un argument vers le type de son paramètre correspondant.  
  
 Si vous passez l’argument [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md), [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] copie parfois la valeur de l’argument dans une variable locale de la procédure au lieu de passer une référence. Dans ce cas, quand la procédure est retournée, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] doit recopier la valeur de la variable locale dans l’argument du code appelant.  
  
 Si une valeur d’argument `ByRef` est copiée dans la procédure, et si l’argument et le paramètre sont du même type, aucune conversion n’est nécessaire. Toutefois, si les types sont différents, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] doit effectuer une conversion dans les deux sens. Si l’un des types est celui de votre classe ou de votre structure, [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] doit le convertir vers et à partir de l’autre type. Cela signifie que vous devez définir des opérateurs de conversion dans les deux sens.  
  
 **ID d’erreur :** BC33037  
  
### Pour corriger cette erreur  
  
-   Si possible, utilisez un argument d’appel du même type que celui du paramètre de procédure, pour que [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] n’ait pas besoin d’effectuer de conversion.  
  
-   Si vous devez appeler la procédure avec un type d’argument différent du type de paramètre, mais n’avez pas besoin de retourner une valeur dans l’argument d’appel, définissez le paramètre sur [ByVal](../Topic/ByVal%20\(Visual%20Basic\).md) au lieu de `ByRef`.  
  
-   Si vous devez retourner une valeur dans l’argument d’appel, définissez l’opérateur de conversion inverse pour que [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)] puisse reconvertir le type vers le type de l’argument d’appel.  
  
## Voir aussi  
 [Procedures](../Topic/Procedures%20in%20Visual%20Basic.md)   
 [Procedure Parameters and Arguments](../Topic/Procedure%20Parameters%20and%20Arguments%20\(Visual%20Basic\).md)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)