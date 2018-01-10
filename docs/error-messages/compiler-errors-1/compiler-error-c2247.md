---
title: Erreur du compilateur C2247 | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2247
dev_langs: C++
helpviewer_keywords: C2247
ms.assetid: 72efa03e-615e-4ef9-aede-0a98654b20fd
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: eac2f90d689bf230b317a0443b5ec79ab40be632
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
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