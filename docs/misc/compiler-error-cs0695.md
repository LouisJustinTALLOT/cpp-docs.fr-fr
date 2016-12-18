---
title: "Erreur du compilateur CS0695 | Microsoft Docs"
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
  - "CS0695"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0695"
ms.assetid: 05f6c8cf-6147-4ac7-84ea-e1f34f8ef9f7
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS0695
'generic type' ne peut pas implémenter 'generic interface' et 'generic interface', car ils peuvent être réunis pour des substitutions de paramètre de type  
  
 Cette erreur se produit quand une classe générique implémente plusieurs paramétrages de la même interface générique et qu’il existe une substitution de paramètre de type qui rendrait les deux interfaces identiques. Pour éviter cette erreur, implémentez une seule des interfaces ou modifiez les paramètres de type pour éviter le conflit.  
  
 L’exemple suivant génère l’erreur CS0695 :  
  
```  
// CS0695.cs // compile with: /target:library interface I<T> { } class G<T1, T2> : I<T1>, I<T2>  // CS0695 { }  
```