---
title: "Erreur du compilateur CS0243 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS0243"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0243"
ms.assetid: 2506e4cb-dc26-46b4-a58c-ab6bf1601144
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0243
L’attribut Conditional n’est pas valide sur 'méthode', car il s’agit d’une méthode override  
  
 L’attribut [Conditional](http://msdn.microsoft.com/fr-fr/e1c4913b-74d0-421a-8a6d-c14b3f0e68fb) n’est pas autorisé sur une méthode marquée avec le mot clé [override](../Topic/override%20\(C%23%20Reference\).md). Pour plus d'informations, consultez [Savoir quand utiliser les mots clés override et new](../Topic/Knowing%20When%20to%20Use%20Override%20and%20New%20Keywords%20\(C%23%20Programming%20Guide\).md).  
  
 Le compilateur ne lie jamais à des méthodes override ; il lie uniquement à la méthode de base et le Common Language Runtime appelle la substitution comme il convient.  
  
 L’exemple suivant génère l’erreur CS0243 :  
  
```  
// CS0243.cs // compile with: /target:library public class MyClass { public virtual void M() {} } public class MyClass2 : MyClass { [System.Diagnostics.ConditionalAttribute("MySymbol")]   // CS0243 // remove Conditional attribute or remove override keyword public override void M() {} }  
```