---
title: "Erreur du compilateur C2156 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C2156"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2156"
ms.assetid: 136f9c67-2c27-4f61-b7e6-ccd202eca697
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C2156
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

pragma doit être à l'extérieur de la fonction  
  
 Un pragma qui doit être spécifié à un niveau global \(en dehors d’un corps de fonction\) se trouve dans une fonction.  
  
 L’exemple suivant génère l’erreur C2156 :  
  
```  
// C2156.cpp #pragma optimize( "l", on )   // OK int main() { #pragma optimize( "l", on )   // C2156 }  
```