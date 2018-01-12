---
title: Compilateur avertissement (niveau 1) C4384 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4384
dev_langs: C++
helpviewer_keywords: C4384
ms.assetid: fafa8eb2-cbfc-4edb-8b0f-511ff5d37ac0
caps.latest.revision: "5"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 10d8be519ee90f2d131df8708b7212164519704c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4384"></a>Avertissement du compilateur (niveau 1) C4384
\#pragma 'make_public' doit uniquement être utilisé dans une portée globale  
  
 Le [make_public](../../preprocessor/make-public.md) pragma a été appliqué de façon incorrecte.  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C4384.  
  
```  
// C4384.cpp  
// compile with: /c /W1  
namespace n {  
   #pragma make_public(N::C)   // C4384  
   namespace N {  
      class C {};  
   }  
}  
```