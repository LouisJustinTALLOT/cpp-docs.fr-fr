---
title: Erreur du compilateur C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 5bf4e2e42b4534d47a2a7d3c9a838c404a99ba68
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62328878"
---
# <a name="compiler-error-c3379"></a>Erreur du compilateur C3379

'classe' : une classe imbriquée ne peut pas avoir de spécificateur d’accès d’assembly dans le cadre de sa déclaration

Lorsqu’il est appliqué à un type managé, telles que la classe ou un struct, le [public](../../cpp/public-cpp.md) et [privé](../../cpp/private-cpp.md) mots clés indiquent si la classe doit être exposée dans les métadonnées de l’assembly. `public` ou `private` ne peut pas être appliqué à une classe imbriquée, qui héritera de l’accès d’assembly de la classe englobante.

Lorsqu’il est utilisé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), le `ref` et `value` mots clés indiquent qu’une classe est managée (consultez [les Classes et Structs](../../extensions/classes-and-structs-cpp-component-extensions.md)).

L’exemple suivant génère l’erreur C3379 :

```
// C3379a.cpp
// compile with: /clr
using namespace System;

public ref class A {
public:
   static int i = 9;

   public ref class BA {   // C3379
   // try the following line instead
   // ref class BA {
   public:
      static int ii = 8;
   };
};

int main() {

   A^ myA = gcnew A;
   Console::WriteLine(myA->i);

   A::BA^ myBA = gcnew A::BA;
   Console::WriteLine(myBA->ii);
}
```
