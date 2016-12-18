---
title: "Avertissement du compilateur (niveau&#160;2) CS0435 | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0435"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0435"
ms.assetid: e70cd8c1-d399-4af8-8b1e-69a1de389aad
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Avertissement du compilateur (niveau&#160;2) CS0435
L’espace de noms 'espace\_de\_noms' dans 'assembly' est en conflit avec le type importé 'type' dans 'assembly'. Utilisation de l’espace de noms défini dans 'assembly'.  
  
 Cet avertissement est émis quand un espace de noms inclus dans un fichier source \(fichier\_2\) est en conflit avec un type importé dans fichier\_1. Le compilateur utilise celui figurant dans le fichier source.  
  
 L’exemple suivant génère l’avertissement CS0435 :  
  
 Compilez d’abord ce fichier :  
  
```  
// CS0435_1.cs // compile with: /t:library public class Util { public class A { } }  
```  
  
 Compilez ensuite ce fichier :  
  
```  
// CS0435_2.cs // compile with: /r:CS0435_1.dll using System; namespace Util { public class A { } } public class Test { public static void Main() { Console.WriteLine(typeof(Util.A)); // CS0435 } }  
```