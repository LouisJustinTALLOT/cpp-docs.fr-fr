---
title: "Erreur du compilateur CS1605 | Microsoft Docs"
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
  - "CS1605"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1605"
ms.assetid: a202d3a9-9777-4902-a7b9-1628640f9433
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# Erreur du compilateur CS1605
Impossible de passer 'variable' comme argument ref ou out, car il est en lecture seule  
  
 Une variable passée comme un paramètre [ref](../Topic/ref%20\(C%23%20Reference\).md) ou [out](../Topic/out%20\(C%23%20Reference\).md) doit être modifiée dans la méthode appelée. Il n’est donc pas possible de passer un paramètre en lecture seule en tant que `ref` ou `out`.