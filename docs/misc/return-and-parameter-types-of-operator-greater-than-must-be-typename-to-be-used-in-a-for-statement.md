---
title: "Les types de retour et de param&#232;tres de &#39;&lt;op&#233;rateur&gt;&#39; doivent &#234;tre &#39;&lt;nom_type&gt;&#39; pour &#234;tre utilis&#233;s dans une instruction &#39;For&#39; | Microsoft Docs"
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
  - "vbc33039"
  - "bc33039"
helpviewer_keywords: 
  - "BC33039"
ms.assetid: 30e8cfa8-c086-474c-a4f0-ad01d01096e2
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les types de retour et de param&#232;tres de &#39;&lt;op&#233;rateur&gt;&#39; doivent &#234;tre &#39;&lt;nom_type&gt;&#39; pour &#234;tre utilis&#233;s dans une instruction &#39;For&#39;
Une boucle `For` spécifie une variable de compteur d’un type qui ne définit pas l’opérateur `+` ou `-` avec des paramètres et une valeur de retour de son propre type.  
  
 La variable de compteur doit être d’un type qui prend en charge l’ajout \(`+`\) et la soustraction \(`-`\) d’opérateurs qui fonctionnent entièrement sur leur type conteneur. Cela signifie que les opérandes et la valeur de retour doivent être du même type que celui de la variable de compteur.  
  
 Si vous utilisez un type de données numérique pour la variable de compteur, les opérateurs `+` et `-` sont pris en charge sur le type conteneur. Si vous utilisez une structure ou une classe définie par l’utilisateur, vous devez définir les deux opérateurs avec des opérandes et une valeur de retour du type de votre structure ou classe.  
  
 **ID d’erreur :** BC33039  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le type de données de la variable de compteur est correctement orthographié.  
  
2.  Si vous utilisez une structure ou une classe définie par l’utilisateur pour la variable de compteur, définissez les opérateurs `+` et `-` qui fonctionnent entièrement sur cette structure ou classe.  
  
## Voir aussi  
 [For...Next, instruction](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)