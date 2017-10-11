---
title: Erreur du compilateur C3189 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3189
dev_langs:
- C++
helpviewer_keywords:
- C3189
ms.assetid: b254de79-931e-4a59-a9f4-1c690d90ca5e
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: ad89c163dfaaa4eaa3a0304160c403977700fe95
ms.contentlocale: fr-fr
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3189"></a>Erreur du compilateur C3189
' typeid\<déclarateur abstrait de type >': cette syntaxe n’est plus pris en charge, utilisez :: typeid à la place  
  
 Une forme obsolète de [typeid](../../windows/typeid-cpp-component-extensions.md) a été utilisé, utilisez la nouvelle forme.  
  
 L’exemple suivant génère l’erreur C3189 :  
  
```  
// C3189.cpp  
// compile with: /clr  
int main() {  
   System::Type^ t  = typeid<System::Object>;   // C3189  
   System::Type^ t2  = System::Object::typeid;   // OK  
}  
```
