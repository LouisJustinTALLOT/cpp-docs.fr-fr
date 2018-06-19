---
title: Compilateur avertissement (niveau 1) C4997 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4997
dev_langs:
- C++
helpviewer_keywords:
- C4997
ms.assetid: d39678fd-0c1a-4104-8a45-9e3f20de0407
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b9b0484beafa364406c5f95ca87048edddaba3f1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33290759"
---
# <a name="compiler-warning-level-1-c4997"></a>Avertissement du compilateur (niveau 1) C4997
'classe' : une coclasse n’implémente pas d’interface COM ou de pseudo-interface  
  
 Une classe marquée avec l’attribut [coclasse](../../windows/coclass.md) n’implémente pas d’interface.  
  
 L’exemple suivant génère l’erreur C4997 :  
  
```  
// C4997.cpp  
// compile with: /WX  
// to resolve this C4997, uncomment all code  
#include <objbase.h>  
  
[ object ]  
__interface I {  
   HRESULT func();  
};  
  
[ coclass ]  
struct C /*: I*/ {  
   /*  
   HRESULT func() {  
      return S_OK;  
   }  
   */  
};   // C4997  
```