---
title: "Erreur du compilateur CS0404 | Microsoft Docs"
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
  - "CS0404"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0404"
ms.assetid: 60bef49e-e0b7-4e9e-aab3-7afc20a19cb8
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0404
'\<' inattendu : les attributs ne peuvent pas être génériques  
  
 Les paramètres de types génériques ne sont pas autorisés dans les attributs. Supprimez le paramètre de type et les crochets.  
  
 L’exemple suivant génère l’erreur CS0404 :  
  
```  
// CS0404.cs [MyAttrib<int>]  // CS0404 class C { public static void Main() { } }  
```