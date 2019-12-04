---
title: Erreur du compilateur C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: e30ed7016ca3a4d4948a08c5c09268e52c9a407d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761671"
---
# <a name="compiler-error-c3181"></a>Erreur du compilateur C3181

'type' : opérande non valide pour l’opérateur

Un paramètre non valide a été passé à l’opérateur [typeid](../../extensions/typeid-cpp-component-extensions.md) . Le paramètre doit être un type managé.

Notez que le compilateur utilise des alias pour les types natifs qui mappent aux types dans le common language runtime.

L’exemple suivant génère l’C3181 :

```cpp
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
