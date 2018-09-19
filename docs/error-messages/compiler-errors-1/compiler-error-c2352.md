---
title: Erreur du compilateur C2352 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2352
dev_langs:
- C++
helpviewer_keywords:
- C2352
ms.assetid: 0efad8cb-659f-4b3e-8f6f-9f8ec44d345c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 29e1c63486c26a2f2ef34dbb1165c581a0c074cd
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46060250"
---
# <a name="compiler-error-c2352"></a>Erreur du compilateur C2352

'class::function' : appel non conforme d'une fonction membre non static

Une fonction membre `static` a appelé une fonction membre non static. Ou bien, une fonction membre non static a été appelée de l'extérieur de la classe en tant que fonction static.

L'exemple suivant génère l'erreur C2352 et montre comment la corriger :

```
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

```
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