---
description: 'En savoir plus sur : erreur du compilateur C3379'
title: Erreur du compilateur C3379
ms.date: 11/04/2016
f1_keywords:
- C3379
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
ms.openlocfilehash: 622a1327eb84d83fa24d8a084e3266183c669120
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97220732"
---
# <a name="compiler-error-c3379"></a>Erreur du compilateur C3379

'classe' : une classe imbriquée ne peut pas avoir de spécificateur d’accès à l’assembly dans le cadre de sa déclaration

En cas d’application à un type managé, tel qu’une classe ou un struct, les mots clés [public](../../cpp/public-cpp.md) et [Private](../../cpp/private-cpp.md) indiquent si la classe sera exposée par le biais des métadonnées de l’assembly. `public` ou `private` ne peuvent pas être appliqués à une classe imbriquée, qui héritera de l’accès à l’assembly de la classe englobante.

En cas d’utilisation avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), les `ref` `value` Mots clés et indiquent qu’une classe est managée (consultez [classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md)).

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
