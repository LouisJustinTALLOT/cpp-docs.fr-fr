---
title: Erreur du compilateur C2352
ms.date: 11/04/2016
f1_keywords:
- C2352
helpviewer_keywords:
- C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
ms.openlocfilehash: 33fdaff31fc9e3fcde1a7101c7858704773ae74c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759982"
---
# <a name="compiler-error-c2352"></a>Erreur du compilateur C2352

'class::function' : appel non conforme d'une fonction membre non static

Une fonction membre `static` a appelé une fonction membre non static. Ou bien, une fonction membre non static a été appelée de l'extérieur de la classe en tant que fonction static.

L'exemple suivant génère l'erreur C2352 et montre comment la corriger :

```cpp
// C2352.cpp
// compile with: /c
class CMyClass {
public:
   static void func1();
   void func2();
   static void func3() {
      func2();   // C2352 calls nonstatic func2
      func1();   // OK calls static func1
   }
};
```

L'exemple suivant génère l'erreur C2352 et montre comment la corriger :

```cpp
// C2352b.cpp
class MyClass {
public:
   void MyFunc() {}
   static void MyFunc2() {}
};

int main() {
   MyClass::MyFunc();   // C2352
   MyClass::MyFunc2();   // OK
}
```
