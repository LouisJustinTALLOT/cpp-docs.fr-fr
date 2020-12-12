---
description: 'En savoir plus sur : erreur du compilateur C3181'
title: Erreur du compilateur C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: b9b9c6e8c6271abbea2d97adf92f33c35eb2028b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174128"
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
