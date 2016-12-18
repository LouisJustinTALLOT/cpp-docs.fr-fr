---
title: "Erreur du compilateur CS0415 | Microsoft Docs"
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
  - "CS0415"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0415"
ms.assetid: 1ed45b02-4568-4af4-b2a6-c8b01230d19a
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0415
L’attribut 'IndexerName' est valide uniquement sur un indexeur qui n’est pas une déclaration de membre d’interface explicite  
  
 Cette erreur se produit si vous utilisez un attribut IndexerName sur un indexeur correspondant à une implémentation explicite d’une interface. Cette erreur peut être évitée grâce à la suppression du nom d’interface de la déclaration de l’indexeur, si possible. Pour plus d’informations, consultez [IndexerNameAttribute, classe](frlrfSystemRuntimeCompilerServicesIndexerNameAttributeClassTopic).  
  
 L’exemple suivant génère l’erreur CS0415 :  
  
```  
// CS0415.cs using System; using System.Runtime.CompilerServices; public interface IA { int this[int index] { get; set; } } public class A : IA { [IndexerName("Item")]  // CS0415 int IA.this[int index] // Try this line instead: // public int this[int index] { get { return 0; } set { } } static void Main() { } }  
```