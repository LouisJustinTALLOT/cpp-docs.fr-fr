---
title: Erreur du compilateur C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 9d99214f3ad7e7db1edc215d94c98e9cf9ec4ca2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742897"
---
# <a name="compiler-error-c3379"></a>Erreur du compilateur C3379

'classe' : une classe imbriquée ne peut pas avoir de spécificateur d’accès à l’assembly dans le cadre de sa déclaration

En cas d’application à un type managé, tel qu’une classe ou un struct, les mots clés [public](../../cpp/public-cpp.md) et [Private](../../cpp/private-cpp.md) indiquent si la classe sera exposée par le biais des métadonnées de l’assembly. `public` ou `private` ne peuvent pas être appliqués à une classe imbriquée, ce qui hérite de l’accès à l’assembly de la classe englobante.

En cas d’utilisation avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), les mots clés `ref` et `value` indiquent qu’une classe est managée (consultez [classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md)).

L’exemple suivant génère l’C3379 :

```cpp
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
