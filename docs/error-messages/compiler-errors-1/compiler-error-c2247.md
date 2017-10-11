---
title: Erreur du compilateur C2247 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2247
dev_langs:
- C++
helpviewer_keywords:
- C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
caps.latest.revision: 13
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 64eafb23ca83cb61ac9b45cf9c84ba69365f8198
ms.contentlocale: fr-fr
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2247"></a>Erreur du compilateur C2247
'identificateur' non accessible, car 'classe' utilise 'spécificateur' pour hériter de 'class'  
  
 `identifier`est héritée d’une classe déclarée avec accès privé ou protégé.  
  
 L’exemple suivant génère l’erreur C2247 :  
  
```  
// C2247.cpp  
class A {  
public:  
   int i;  
};  
class B : private A {};    // B inherits a private A  
class C : public B {} c;   // so even though C's B is public  
int j = c.i;               // C2247, i not accessible  
```  
  
 Cette erreur peut également être due à la mise en conformité du compilateur pour Visual Studio .NET 2003 : contrôle d’accès avec membres protégés. Un membre protégé (n) peut uniquement être accessible via une fonction membre d’une classe qui hérite de la classe (A) dont il (n) est un membre (B).  
  
 Pour le code qui est valide dans Visual Studio .NET 2003 et les versions de Visual Studio .NET de Visual C++, déclarez le membre soit une fonction friend du type. L’héritage public peut également être utilisé.  
  
```  
// C2247b.cpp  
// compile with: /c  
// C2247 expected  
class A {  
public:  
   void f();  
   int n;  
};  
  
class B: protected A {  
   // Uncomment the following line to resolve.  
   // friend void A::f();  
};  
  
void A::f() {  
   B b;  
   b.n;  
}  
```  
  
 L’erreur C2247 peut également être due à la mise en conformité du compilateur pour Visual Studio .NET 2003 : classes de base privées maintenant inaccessibles. Une classe (A) qui est une classe de base privée pour un type n’a pas (B) doit être accessible à un type (C) qui utilise B comme classe de base.  
  
 Pour le code qui est valide dans Visual Studio .NET 2003 et les versions de Visual Studio .NET de Visual C++, utilisez l’opérateur de portée.  
  
```  
// C2247c.cpp  
// compile with: /c  
struct A {};  
  
struct B: private A {};  
  
struct C : B {  
   void f() {  
      A *p1 = (A*) this;   // C2247  
      // try the following line instead  
      // ::A *p2 = (::A*) this;  
   }  
};  
```
