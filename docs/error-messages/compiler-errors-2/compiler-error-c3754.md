---
title: "Erreur du compilateur C3754 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3754"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3754"
ms.assetid: 14b877bc-9277-40ec-af1c-196a58b45f10
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Erreur du compilateur C3754
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'constructeur délégué : la fonction membre 'fonction' ne peut pas être appelée sur une instance de type 'type'  
  
 Vous avez effectué un appel d'une fonction par l'intermédiaire d'un pointeur ayant un type qui ne contient pas la fonction.  
  
 L'exemple suivant génère l'erreur C3754 :  
  
```  
// C3754a.cpp  
// compile with: /clr  
using namespace System;  
  
delegate void MyDel();  
  
interface class MyInterface {};  
  
ref struct MyClass : MyInterface {  
   void f() {}  
};  
  
int main() {  
   MyInterface^ p = gcnew MyClass;  
   MyDel^ q = gcnew MyDel(p, &MyClass::f);   // C3754  
   // try the following line instead  
//   MyDel^ q = gcnew MyDel(safe_cast<MyClass^>(p), &MyClass::f);  
}  
```  
  
 L'exemple suivant génère l'erreur C3754 :  
  
```  
// C3754b.cpp  
// compile with: /clr:oldSyntax  
#using <mscorlib.dll>  
using namespace System;  
  
__delegate void MyDel();  
  
__gc __interface MyInterface {};  
  
__gc struct MyClass : MyInterface {  
   void f() {}  
};  
  
int main() {  
   MyInterface* p = new MyClass;  
   MyDel* q = new MyDel(p, &MyClass::f);   // C3754  
   // try the following line instead  
   // MyDel* q = new MyDel(__try_cast<MyClass*>(p), &MyClass::f);  
}  
```