---
title: Compilateur avertissement (niveau 2) C4250 | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4250
dev_langs:
- C++
helpviewer_keywords:
- C4250
ms.assetid: d47f7249-6b5a-414b-b2d4-56e5d246a782
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4b0a49f42dec57677149ab5c36cfc1ab99822cc4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291357"
---
# <a name="compiler-warning-level-2-c4250"></a>Avertissement du compilateur (niveau 2) C4250
'classe1' : hérite de 'classe2::membre' via la dominance  
  
 Deux membres ou plus ont le même nom. Celui de `class2` est héritée car il s’agit d’une classe de base pour les autres classes qui contenaient ce membre.  
  
 Pour supprimer l’erreur C4250, utilisez le [avertissement](../../preprocessor/warning.md) pragma.  
  
 Étant donné que la classe de base virtuelle est partagée entre plusieurs classes dérivées, un nom dans une classe dérivée domine un nom dans une classe de base. Par exemple, la hiérarchie de classe suivante, il existe deux définitions de func héritées dans un losange : l’instance ::Func() via la classe faible et le dominante :: func() via la classe dominante. Un appel non qualifié de func() via un objet de classe en losange, appelle toujours l’instance dominate::func.  Si la classe faible devait introduire une instance de func(), ni dépasse celle de définition et l’appel est marqué comme ambiguë.  
  
```  
// C4250.cpp  
// compile with: /c /W2  
#include <stdio.h>  
struct vbc {  
   virtual void func() { printf("vbc::func\n"); }  
};  
  
struct weak : public virtual vbc {};  
  
struct dominant : public virtual vbc {  
   void func() { printf("dominant::func\n"); }  
};  
  
struct diamond : public weak, public dominant {};  
  
int main() {  
   diamond d;  
   d.func();   // C4250  
}  
```  
  
## <a name="example"></a>Exemple  
 L’exemple suivant génère l’erreur C4250.  
  
```  
// C4250_b.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
class A {  
public:  
   virtual operator int () {  
      return 2;  
   }  
};  
  
class B : virtual public A {  
public:  
   virtual operator int () {  
      return 3;  
   }  
};  
  
class C : virtual public A {};  
  
class E : public B, public C {};   // C4250  
  
int main() {  
   E eObject;  
   cout << eObject.operator int() << endl;  
}  
```  
  
## <a name="example"></a>Exemple  
 Cet exemple montre une situation plus complexe. L’exemple suivant génère l’erreur C4250.  
  
```  
// C4250_c.cpp  
// compile with: /W2 /EHsc  
#include <iostream>  
using namespace std;  
  
class V {  
public:  
   virtual int f() {  
      return 1024;  
   }  
};  
  
class B : virtual public V {  
public:  
   int b() {  
      return f(); // B::b() calls V::f()  
   }  
};  
  
class M : virtual public V {  
public:  
   int f() {  
      return 7;  
   }  
};  
  
// because of dominance, f() is M::f() inside D,  
// changing the meaning of B::b's f() call inside a D  
class D : public B, public M {};   // C4250  
  
int main() {  
   D d;  
   cout << "value is: " << d.b();   // invokes M::f()  
}  
```