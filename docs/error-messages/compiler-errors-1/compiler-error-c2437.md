---
title: Erreur du compilateur C2437 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2437
dev_langs:
- C++
helpviewer_keywords:
- C2437
ms.assetid: 2d2b3c6c-856a-4b27-ae10-64813b3e5483
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc9c619ac361fcbe2d095407b4030a2e38ada8ad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33224422"
---
# <a name="compiler-error-c2437"></a>Erreur du compilateur C2437
'identificateur' : déjà initialisé  
  
 Un objet peut être initialisé qu’une seule fois.  
  
 L’exemple suivant génère l’erreur C2437 :  
  
```  
// C2437.cpp  
// compile with: /c  
class A {  
public:  
   A(int i) {}  
};  
  
class B : A {  
   B() : A(1), A(2) {}   // C2437  
   B() : A(1) {}   // OK  
};  
```