---
title: "Le constructeur d’attribut a un param&#232;tre &#39;ByRef&#39; de type &#39;&lt;nom_type&gt;&#39;&#160;; impossible d’utiliser les constructeurs avec des param&#232;tres byref pour appliquer l’attribut | Microsoft Docs"
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
  - "bc36006"
  - "vbc36006"
helpviewer_keywords: 
  - "BC36006"
ms.assetid: 4c4e991f-3839-4196-bcfb-eb8464aa55e5
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Le constructeur d’attribut a un param&#232;tre &#39;ByRef&#39; de type &#39;&lt;nom_type&gt;&#39;&#160;; impossible d’utiliser les constructeurs avec des param&#232;tres byref pour appliquer l’attribut
Un attribut est appliqué à un élément de programmation à l’aide d’un constructeur d’attribut qui accepte un paramètre `ByRef`.  
  
 Les attributs sont appliqués au moment de la compilation, et le compilateur doit passer des valeurs concrètes au constructeur d’attribut. Un paramètre `ByRef` prend comme valeur un pointeur qui ne peut pas être évalué au moment de la compilation.  
  
 Vous pouvez définir un constructeur d’attribut qui accepte un paramètre `ByRef` et vous pouvez l’utiliser à différentes fins, telles que l’héritage, par exemple. Toutefois, quand vous appliquez l’attribut, vous devez utiliser un constructeur qui n’accepte aucun paramètre `ByRef`.  
  
 **ID d’erreur :** BC36006  
  
### Pour corriger cette erreur  
  
-   Appliquez l’attribut à l’aide d’un constructeur qui n’accepte aucun paramètre `ByRef`, ou n’appliquez pas d’attribut.  
  
## Voir aussi  
 [NOT IN BUILD : Vue d’ensemble des attributs en Visual Basic](http://msdn.microsoft.com/fr-fr/0d0cff64-892d-4f57-83bd-bef388553d4f)   
 [NOT IN BUILD : Application des attributs](http://msdn.microsoft.com/fr-fr/2b1703ed-4437-49b3-bc0b-568094324f47)   
 [Passing Arguments by Value and by Reference](../Topic/Passing%20Arguments%20by%20Value%20and%20by%20Reference%20\(Visual%20Basic\).md)   
 [ByRef](../Topic/ByRef%20\(Visual%20Basic\).md)