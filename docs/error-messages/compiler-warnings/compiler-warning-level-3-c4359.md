---
title: "Avertissement du compilateur (niveau 3) C4359 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4359"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4359"
ms.assetid: d8fe993c-ef82-45a0-a43d-c29f9d1bacdb
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Avertissement du compilateur (niveau 3) C4359
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'type' : l'alignement réel \(8\) est supérieur à la valeur spécifiée dans \_\_declspec\(align\(\)\)  
  
 L'alignement spécifié pour un type est inférieur à celui du type de l'une de ses données membres.  Pour plus d'informations, consultez [align](../../cpp/align-cpp.md).  
  
## Exemple  
 L'exemple suivant génère l'erreur C4359 :  
  
```  
// C4359.cpp  
// compile with: /W3 /c  
struct __declspec(align(8)) C8 { __int64 i; };  
struct __declspec(align(4)) C4  { C8 m8; };   // C4359  
struct __declspec(align(8)) C8_b  { C8 m8; };   // OK  
struct __declspec(align(16)) C16  { C8 m8; };   // OK  
```