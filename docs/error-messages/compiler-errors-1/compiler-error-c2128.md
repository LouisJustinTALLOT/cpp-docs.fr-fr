---
title: Erreur du compilateur C2128 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- c2128
dev_langs:
- C++
helpviewer_keywords:
- C2128
ms.assetid: 08cbf734-75b3-49f2-9026-9b319947612d
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: d0739af6c84b2dc1a7f86c5cb4843ce66e85bf85
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2128"></a>Erreur du compilateur C2128
'fonction' : alloc_text/same_seg applicable qu’aux fonctions avec liaison C  
  
 `pragma``alloc_text` peut uniquement être utilisée avec des fonctions déclarées comme ayant une liaison C.  
  
 L’exemple suivant génère C2128 :  
  
```  
// C2128.cpp  
// compile with: /c  
  
// Delete the following line to resolve.  
void func();  
// #pragma alloc_text("my segment", func)   // C2128  
  
extern "C" {  
void func();  
}  
  
#pragma alloc_text("my segment", func)  
void func() {}  
```
