---
title: Erreur du compilateur C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: ca378c3e0ce88b454cb89fc08470a277a7be6f47
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755224"
---
# <a name="compiler-error-c2694"></a>Erreur du compilateur C2694

'override' : la fonction virtuelle de substitution a moins de spécifications d’exception restrictives que la fonction membre virtuelle’base’de la classe de base

Une fonction virtuelle a été remplacée, mais sous [/za](../../build/reference/za-ze-disable-language-extensions.md), la fonction de substitution avait une spécification d' [exception](../../cpp/exception-specifications-throw-cpp.md)moins restrictive.

L’exemple suivant génère l’C2694 :

```cpp
// C2694.cpp
// compile with: /Za /c
class MyBase {
public:
   virtual void f(void) throw(int) {
   }
};

class Derived : public MyBase {
public:
   void f(void) throw(...) {}   // C2694
   void f2(void) throw(int) {}   // OK
};
```
