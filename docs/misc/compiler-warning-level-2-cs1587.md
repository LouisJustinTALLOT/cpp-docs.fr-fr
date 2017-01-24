---
title: "Avertissement du compilateur (niveau&#160;2) CS1587 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1587"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1587"
ms.assetid: b27c2009-d485-43fd-a649-fbc15570d256
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS1587
Le commentaire XML n'est pas placé dans un élément valide du langage  
  
 Les balises recommandées pour les commentaires de documentation ne sont pas autorisées sur tous les éléments de langage. Par exemple, une balise n’est pas autorisée sur un espace de noms. Pour plus d’informations sur les commentaires XML, consultez [Balises recommandées pour les commentaires de documentation](../Topic/Recommended%20Tags%20for%20Documentation%20Comments%20\(C%23%20Programming%20Guide\).md).  
  
## Exemple  
 L’exemple suivant génère l’avertissement CS1587 :  
  
```  
// CS1587.cs // compile with: /W:2 /doc:x.xml /// <summary>test</summary>   // CS1587, tag not allowed on namespace namespace MySpace { class MyClass { public static void Main() { } } }  
```