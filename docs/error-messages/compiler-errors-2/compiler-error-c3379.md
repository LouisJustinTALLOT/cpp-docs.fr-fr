---
title: Erreur du compilateur C3379 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3379
dev_langs:
- C++
helpviewer_keywords:
- C3379
ms.assetid: a66c2c4e-091c-4426-9cde-7c4cfb2ffce1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f90a4ccc17e63c21d4b6fb26e607450849f27b48
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109325"
---
# <a name="compiler-error-c3379"></a>Erreur du compilateur C3379

'classe' : une classe imbriquée ne peut pas avoir de spécificateur d’accès d’assembly dans le cadre de sa déclaration

Lorsqu’il est appliqué à un type managé, telles que la classe ou un struct, le [public](../../cpp/public-cpp.md) et [privé](../../cpp/private-cpp.md) mots clés indiquent si la classe doit être exposée dans les métadonnées de l’assembly. `public` ou `private` ne peut pas être appliqué à une classe imbriquée, qui héritera de l’accès d’assembly de la classe englobante.

Lorsqu’il est utilisé avec [/CLR](../../build/reference/clr-common-language-runtime-compilation.md), le `ref` et `value` mots clés indiquent qu’une classe est managée (consultez [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md)).

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
