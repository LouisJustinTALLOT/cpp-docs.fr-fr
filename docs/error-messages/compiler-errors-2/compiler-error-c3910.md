---
title: Erreur du compilateur C3910 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3910
dev_langs:
- C++
helpviewer_keywords:
- C3910
ms.assetid: cfcbe620-b463-463b-95ea-2d60ad33ebb5
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 7a1bae6f59e48f1294e657f35f7dae8ac9e937d4
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3910"></a>Erreur du compilateur C3910
'événement' : doit définir 'méthode' membre  
  
 Un événement a été défini, mais il ne contenait pas la méthode d’accesseur spécifiée requise.  
  
 Pour plus d’informations, consultez [événement](../../windows/event-cpp-component-extensions.md).  
  
 L’exemple suivant génère l’erreur C3910 :  
  
```  
// C3910.cpp  
// compile with: /clr /c  
delegate void H();  
ref class X {  
   event H^ E {  
      // uncomment the following lines  
      // void add(H^) {}  
      // void remove( H^ h ) {}  
      // void raise( ) {}  
   };   // C3910  
  
   event H^ E2; // OK data member  
};  
```
