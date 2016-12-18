---
title: "Avertissement du compilateur (niveau 1) C4229 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4229"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4229"
ms.assetid: aadfc83b-1e5f-4229-bd0a-9c10a5d13182
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Avertissement du compilateur (niveau 1) C4229
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

anachronisme utilisé : modificateurs de données ignorés  
  
 L'utilisation d'un modificateur Microsoft tel que `__cdecl` sur une déclaration de données est un anachronisme.  
  
## Exemple  
  
```  
// C4229.cpp  
// compile with: /W1 /LD  
int __cdecl counter;   // C4229 cdecl ignored  
```