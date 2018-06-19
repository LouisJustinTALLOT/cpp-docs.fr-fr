---
title: Erreur du compilateur C2792 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2792
dev_langs:
- C++
helpviewer_keywords:
- C2792
ms.assetid: 392cf748-4f5e-4e62-a364-3118d5658408
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 608d7b799f9f5dc4cf4717f46f61af3e1c5240b6
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33236988"
---
# <a name="compiler-error-c2792"></a>Erreur du compilateur C2792
'super' : ce mot clé doit être suivi par ' ::'  
  
 Le seul jeton qui peut suivre le mot clé `__super` est `::`.  
  
 L’exemple suivant génère l’erreur C2792 :  
  
```  
// C2792.cpp  
struct B {  
   void mf();  
};  
  
struct D : B {  
   void mf() {  
      __super.();   // C2792  
  
      // try the following line instead  
      // __super::mf();  
   }  
};  
```