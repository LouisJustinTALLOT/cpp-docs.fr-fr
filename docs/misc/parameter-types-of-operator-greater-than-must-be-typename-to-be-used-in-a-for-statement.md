---
title: "Les types de param&#232;tres de &#39;&lt;op&#233;rateur&gt;&#39; doivent &#234;tre &#39;&lt;nom_type&gt;&#39; pour &#234;tre utilis&#233;s dans une instruction &#39;For&#39; | Microsoft Docs"
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
  - "BC33040"
  - "vbc33040"
helpviewer_keywords: 
  - "BC33040"
ms.assetid: bffbb812-0d69-47e4-96c5-01882722ccdb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Les types de param&#232;tres de &#39;&lt;op&#233;rateur&gt;&#39; doivent &#234;tre &#39;&lt;nom_type&gt;&#39; pour &#234;tre utilis&#233;s dans une instruction &#39;For&#39;
Une boucle `For` spécifie une variable de compteur d’un type qui ne définit pas l’opérateur `>=` ou `<=` avec des paramètres de son propre type.  
  
 Le type de la variable de compteur doit prendre en charge les opérateurs supérieur ou égal à \(`>=`\) et inférieur ou égal à \(`<=`\) qui comparent leur type conteneur. Cela signifie que les opérandes doivent être du même type que celui de la variable de compteur.  
  
 Si vous utilisez un type de données numérique pour la variable de compteur, les opérateurs `>=` et `<=` sont pris en charge sur le type conteneur. Si vous utilisez une structure ou une classe définie par l’utilisateur, vous devez définir les deux opérateurs avec des opérandes du type de votre structure ou classe.  
  
 **ID d’erreur :** BC33040  
  
### Pour corriger cette erreur  
  
1.  Vérifiez que le type de données de la variable de compteur est correctement orthographié.  
  
2.  Si vous utilisez une structure ou une classe définie par l’utilisateur pour la variable de compteur, définissez les opérateurs `>=` et `<=` qui comparent cette structure ou cette classe.  
  
## Voir aussi  
 [For...Next, instruction](../Topic/For...Next%20Statement%20\(Visual%20Basic\).md)   
 [Operator Procedures](../Topic/Operator%20Procedures%20\(Visual%20Basic\).md)   
 [Operator Statement](../Topic/Operator%20Statement.md)   
 [How to: Define an Operator](../Topic/How%20to:%20Define%20an%20Operator%20\(Visual%20Basic\).md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)