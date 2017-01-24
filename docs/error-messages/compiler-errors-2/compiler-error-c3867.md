---
title: "Erreur du compilateur C3867 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3867"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3867"
ms.assetid: bc5de03f-e01a-4407-88c3-2c63f0016a1e
caps.latest.revision: 22
caps.handback.revision: 22
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Erreur du compilateur C3867
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'fonction' : liste d'arguments manquante dans l'appel de fonction ; utilisez '&fonction' pour créer un pointeur vers membre  
  
 Vous avez essayé de prendre l'adresse d'une fonction membre sans qualifier la fonction membre avec son nom de classe et l'opérateur d'adresse.  
  
 Cette erreur peut également être due à la mise en conformité du compilateur pour Visual C\+\+ 2005 : conformité pointeur vers membre améliorée.  Le code compilé avant Visual C\+\+ 2005 génère désormais l'erreur C3867.  
  
## Exemple  
 L'erreur C3867 peut provenir du compilateur avec une résolution suggérée équivoque.  Si possible, utilisez la classe la plus dérivée.  
  
 L'exemple suivant génère l'erreur C3867 et montre comment la corriger.  
  
```  
// C3867_1.cpp  
// compile with: /c  
struct Base {   
protected:   
   void Test() {}  
};  
  
class Derived : public Base {   
   virtual void Bar();  
};  
  
void Derived::Bar() {  
   void (Base::*p1)() = Test;   // C3867  
   &Derived::Test;   // OK  
}  
```  
  
## Exemple  
 L'exemple suivant génère l'erreur C3867 et montre comment la corriger.  
  
```  
// C3867_2.cpp  
#include<stdio.h>  
  
struct S {  
   char *func() {  
      return "message";  
   }  
};  
  
class X {  
public:  
   void f() {}  
};  
  
int main() {  
   X::f;   // C3867  
  
   // OK  
   X * myX = new X;  
   myX->f();  
  
   S s;  
   printf_s("test %s", s.func);   // C3867  
   printf_s("test %s", s.func());   // OK  
}  
```  
  
## Exemple  
 L'exemple suivant génère l'erreur C3867 et montre comment la corriger.  
  
```  
// C3867_3.cpp  
class X {  
public:  
   void mf(){}  
};  
  
int main() {  
   void (X::*pmf)() = X::mf;   // C3867  
  
   // try the following line instead  
   void (X::*pmf2)() = &X::mf;  
}  
```  
  
## Exemple  
 L'exemple suivant génère l'erreur C3867.  
  
```  
// C3867_4.cpp  
// compile with: /c  
class A {  
public:  
   void f(int) {}  
  
   typedef void (A::*TAmtd)(int);  
  
   struct B {  
      TAmtd p;  
   };  
  
   void g() {  
      B b1;  
      b1.p = f;   // C3867  
   }  
};  
```  
  
## Exemple  
 L'exemple suivant génère l'erreur C3867.  
  
```  
// C3867_5.cpp  
// compile with: /EHsc  
#include <iostream>  
  
class Testpm {  
public:  
   void m_func1() {  
      std::cout << m_num << "\tm_func1\n";   
    }  
  
   int m_num;  
   typedef void (Testpm::*pmfn1)();  
   void func(Testpm* p);  
};  
  
void Testpm::func(Testpm* p) {  
   pmfn1 s = m_func1;   // C3867  
   pmfn1 s2 = &Testpm::m_func1;   // OK  
   (p->*s2)();  
}  
  
int main() {  
   Testpm *pTestpm = new Testpm;  
   pTestpm->m_num = 10;  
  
   pTestpm->func(pTestpm);  
}  
```