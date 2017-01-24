---
title: "Option Strict On interdit les conversions implicites de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39; | Microsoft Docs"
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
  - "bc30512"
  - "vbc30512"
helpviewer_keywords: 
  - "BC30512"
ms.assetid: b9756d48-05fa-4027-8a80-b4a0ef92099d
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Option Strict On interdit les conversions implicites de &#39;&lt;type1&gt;&#39; en &#39;&lt;type2&gt;&#39;
Vous avez tenté de convertir un type en un autre type qui ne peut peut\-être pas contenir la valeur, comme un `Long` en `Integer`, tandis que le commutateur de vérification de type \([Option Strict Statement](../Topic/Option%20Strict%20Statement.md)\) a la valeur `On`.  
  
 Ce type de conversion, appelé *conversion restrictive*, est susceptible d’échouer au moment de l’exécution. Pour cette raison, `Option Strict On` interdit les conversions restrictives implicites.  
  
 **ID d’erreur :** BC30512  
  
### Pour corriger cette erreur  
  
1.  Déterminez si une conversion de n’importe quel type existe de `<type1>` à `<type2>`. Si les deux sont des types élémentaires [!INCLUDE[vbprvb](../dotnet/includes/vbprvb_md.md)], ou des instances de classes, vous pouvez généralement effectuer cette détermination en consultant la table dans [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md).  
  
2.  S’il existe uniquement une conversion restrictive de `<type1>` à `<type2>`, vous devez utiliser un cast explicite. Les mots clés [CType, fonction](../Topic/CType%20Function%20\(Visual%20Basic\).md) et [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md) lèvent une exception runtine en cas d’échec de la conversion. Le mot clé [TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md) s’applique uniquement aux types référence et retourne [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md) en cas d’échec de la conversion.  
  
3.  Si une conversion restrictive existe et que votre programme peut tolérer une défaillance du runtime, ou si vous avez la certitude qu’aucune défaillance du runtime ne peut se produire, vous pouvez spécifier `Option Strict Off` au début de votre code source. Mais vous devez toujours englober la conversion dans un bloc [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md) pour éviter des résultats inattendus ou l’arrêt prématuré de votre programme.  
  
4.  Si aucune conversion n’est effectuée de `<type1>` à `<type2>`, vous devez réévaluer la logique de votre programme. Vous pouvez peut\-être écrire du code qui assigne des valeurs à `<type2>` correspondant aux valeurs anticipées de `<type1>`.  
  
5.  Si aucune conversion n’est effectuée de `<type1>` à `<type2>` et que l’un des types est une classe ou une structure que vous avez définie, vous pouvez peut\-être définir un opérateur de conversion de ce type vers l’autre type ou à partir de celui\-ci. Pour plus d'informations, consultez [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md).  
  
6.  En règle générale, il est recommandé de ne pas utiliser de conversions restrictives, sauf si vous pouvez intercepter les défaillances dans un bloc `Catch` et les traiter de manière efficace.  
  
## Voir aussi  
 [Option Strict Statement](../Topic/Option%20Strict%20Statement.md)   
 [Widening and Narrowing Conversions](../Topic/Widening%20and%20Narrowing%20Conversions%20\(Visual%20Basic\).md)   
 [CType, fonction](../Topic/CType%20Function%20\(Visual%20Basic\).md)   
 [DirectCast Operator](../Topic/DirectCast%20Operator%20\(Visual%20Basic\).md)   
 [TryCast Operator](../Topic/TryCast%20Operator%20\(Visual%20Basic\).md)   
 [Nothing](../Topic/Nothing%20\(Visual%20Basic\).md)   
 [Try...Catch...Finally Statement](../Topic/Try...Catch...Finally%20Statement%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)