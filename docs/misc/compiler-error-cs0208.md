---
title: "Erreur du compilateur CS0208 | Microsoft Docs"
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
  - "CS0208"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0208"
ms.assetid: 03534893-1522-4dab-9822-8b9ed97b3bd0
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0208
Impossible de prendre l’adresse, d’obtenir la taille ou de déclarer un pointeur vers un type managé \('type'\)  
  
 Même en cas d’utilisation avec le mot clé [unsafe](../Topic/unsafe%20\(C%23%20Reference\).md), il n’est pas autorisé de prendre l’adresse d’un objet managé, d’obtenir la taille d’un objet managé ou de déclarer un pointeur vers un type managé. Un type managé est :  
  
-   tout type référence ;  
  
-   tout struct qui contient un type référence comme un champ ou une propriété.  
  
 Pour plus d’informations, consultez [Pointeurs et code unsafe](../Topic/Unsafe%20Code%20and%20Pointers%20\(C%23%20Programming%20Guide\).md) et [sizeof](../Topic/sizeof%20\(C%23%20Reference\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0208 :  
  
```  
// CS0208.cs // compile with: /unsafe class myClass { public int a = 98; } struct myProblemStruct { string s; float f; } struct myGoodStruct { int i; float f; } public class MyClass { unsafe public static void Main() { // myClass is a class, a managed type. myClass s = new myClass(); myClass* s2 = &s;    // CS0208 // The struct contains a string, a managed type. int i = sizeof(myProblemStruct); //CS0208 // The struct contains only value types. i = sizeof(myGoodStruct); //OK } }  
  
```  
  
## Voir aussi  
 [sizeof](../Topic/sizeof%20\(C%23%20Reference\).md)