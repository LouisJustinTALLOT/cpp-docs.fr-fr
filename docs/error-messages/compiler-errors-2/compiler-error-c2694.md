---
description: 'En savoir plus sur : erreur du compilateur C2694'
title: Erreur du compilateur C2694
ms.date: 11/04/2016
f1_keywords:
- C2694
helpviewer_keywords:
- C2694
ms.assetid: 8dc2cec2-67ae-4e16-8c0c-374425aca8bc
ms.openlocfilehash: 4da5362a9c20a2bae10d2a201650f4312d455164
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97326655"
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
