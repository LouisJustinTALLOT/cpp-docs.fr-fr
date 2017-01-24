---
title: "Erreur du compilateur CS0264 | Microsoft Docs"
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
  - "CS0264"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0264"
ms.assetid: a8a87185-5915-4b0d-a8cd-2f129ea51b8f
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0264
Les déclarations partielles de 'type' doivent avoir les mêmes noms de paramètre de type dans le même ordre  
  
 Cette erreur se produit si vous définissez un type générique dans des déclarations partielles alors que l’ordre ou les noms des paramètres de type ne sont pas les mêmes dans toutes les déclarations partielles. Pour résoudre cette erreur, vérifiez les paramètres de type de chaque déclaration partielle et assurez\-vous que les mêmes noms et le même ordre sont utilisés pour tous les paramètres. Pour plus d’informations, consultez [Classes et méthodes partielles](../Topic/Partial%20Classes%20and%20Methods%20\(C%23%20Programming%20Guide\).md) et [Paramètres de type générique](../Topic/Generic%20Type%20Parameters%20\(C%23%20Programming%20Guide\).md).  
  
## Exemple  
 L’exemple suivant génère l’erreur CS0264 :  
  
```  
// CS0264.cs partial class MyClass<T>  // CS0264 { } partial class MyClass <MyType> { }  
```