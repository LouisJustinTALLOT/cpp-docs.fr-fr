---
title: Erreur du compilateur C3192
ms.date: 11/04/2016
f1_keywords:
- C3192
helpviewer_keywords:
- C3192
ms.assetid: 8b0083d4-706f-46f6-858a-e1d9af464cf8
ms.openlocfilehash: 685657857b2ed41c29c704633b07dc677fc32fc3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50481105"
---
# <a name="compiler-error-c3192"></a>Erreur du compilateur C3192

Erreur de syntaxe : ' ^' n’est pas un opérateur préfixé (voulez-vous utiliser ' *'?)

Un handle ne peut pas être utilisé comme un opérateur de déréférencement.

L’exemple suivant génère l’erreur C3192 :

```
// C3192.cpp
// compile with: /clr
using namespace System;

ref class MyClass {
public:
   MyClass () {}
   MyClass(MyClass%) {}
};

int main() {
   MyClass ^ s = gcnew MyClass;
   MyClass b = ^s;   // C3192

   // OK
   MyClass b2 = *s;
}
```