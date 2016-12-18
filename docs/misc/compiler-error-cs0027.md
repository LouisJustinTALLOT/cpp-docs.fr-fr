---
title: "Erreur du compilateur CS0027 | Microsoft Docs"
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
  - "CS0027"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0027"
ms.assetid: 3a599876-9643-4c68-9457-3306858a73e9
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0027
Le mot clé 'this' n'est pas disponible dans le contexte actuel  
  
 Le mot clé [this](../Topic/this%20\(C%23%20Reference\).md) a été trouvé en dehors d’une propriété, d’une méthode ou d’un constructeur.  
  
 Pour corriger cette erreur, vous devez modifier l’instruction de manière à éliminer l’utilisation du mot clé `this` et\/ou déplacer l’instruction, ou une partie de celle\-ci, à l’intérieur d’une propriété, d’une méthode ou d’un constructeur.  
  
 L’exemple suivant génère l’erreur CS0027 :  
  
```  
using System; using System.Collections.Generic; using System.Text; namespace ConsoleApplication3 { class MyClass { int err1 = this.Fun() + 1;  // CS0027 public int Fun() { return 10; } public void Test() { // valid use of this int err = this.Fun() + 1; Console.WriteLine(err); } public static void Main() { MyClass c = new MyClass(); c.Test(); } } }  
```