---
title: "Erreur du compilateur C2506 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2506"
ms.assetid: cfed21cd-2404-46f2-985e-d0c2c3820830
caps.latest.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 5
---
# Erreur du compilateur C2506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'membre' : '\_\_declspec\(modifier\)' ne peut pas être appliqué à ce symbole  
  
 Vous ne pouvez pas déclarer par processus ou par appdomain les membres static d'une classe managée.  
  
 Pour plus d'informations, consultez [appdomain](../../cpp/appdomain.md).  
  
## Exemple  
 L'exemple suivant génère l'erreur C2506 :  
  
```  
// C2506.cpp  
// compile with: /clr /c  
ref struct R {  
   __declspec(process) static int n;   // C2506  
   int o;   // OK  
};  
```