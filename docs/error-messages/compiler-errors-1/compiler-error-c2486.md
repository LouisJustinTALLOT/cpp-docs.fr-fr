---
title: Erreur du compilateur C2486 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2486
dev_langs:
- C++
helpviewer_keywords:
- C2486
ms.assetid: 436da349-6461-4e32-bfca-4f3e620108e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 856d17d9ec816c8216553eca5bb273349ca0040e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197284"
---
# <a name="compiler-error-c2486"></a>Erreur du compilateur C2486
'__LOCAL_SIZE' uniquement autorisé dans une fonction avec l’attribut 'naked'  
  
 Dans les fonctions d’assembly inline, le nom `__LOCAL_SIZE` est réservée pour les fonctions déclarées avec le [naked](../../cpp/naked-cpp.md) attribut.  
  
 L’exemple suivant génère C2486 :  
  
```  
// C2486.cpp  
// processor: x86  
void __declspec(naked) f1() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE  
   }  
}  
void f2() {  
   __asm {  
      mov   eax,   __LOCAL_SIZE   // C2486  
   }  
}  
```