---
title: Erreur du compilateur C2139 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2139
dev_langs:
- C++
helpviewer_keywords:
- C2139
ms.assetid: 31e047c0-5bf9-46c2-b6de-b627ea6a5768
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 4cbd836061fc87be1ab1be8bfab395132cfc03e8
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2139"></a>Erreur du compilateur C2139
'type' : une classe non définie n’est pas autorisée en tant qu’argument pour un trait de type intrinsèque du compilateur 'trait'  
  
 Un argument non valide a été passé à un trait de type.  
  
 Pour plus d’informations, consultez [prise en charge du compilateur pour les Type Traits](../../windows/compiler-support-for-type-traits-cpp-component-extensions.md).  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère C2139.  
  
```  
// C2139.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
template <class T>  
struct is_polymorphic {  
   static const bool value = __is_polymorphic(T);  
};  
  
class C;  
class D {};  
  
class E {  
public:  
   virtual void Test() {}  
};  
  
int main() {  
   cout << is_polymorphic<C>::value << endl;   // C2139  
   cout << is_polymorphic<D>::value << endl;   // OK  
   cout << is_polymorphic<E>::value << endl;   // OK  
}  
```
