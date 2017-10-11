---
title: Erreur du compilateur C2312 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C2312
dev_langs:
- C++
helpviewer_keywords:
- C2312
ms.assetid: c8bcfd06-12c1-4323-bb53-ba392d36daa4
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 5d660a82b0bdf1b77848c993f6796ac3fa45e1ff
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2312"></a>Erreur du compilateur C2312
« exception1 » : interceptée par « exception2 » à la ligne  
  
 Deux gestionnaires interceptent le même type d’exception.  
  
 L’exemple suivant génère l’erreur C2312 :  
  
```  
// C2312.cpp  
// compile with: /EHsc  
#include <eh.h>  
int main() {  
    try {  
        throw "ooops!";  
    }  
    catch( signed int ) {}  
    catch( int ) {}   // C2312  
}  
```
