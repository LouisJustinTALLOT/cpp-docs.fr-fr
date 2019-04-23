---
title: Erreur du compilateur C3181
ms.date: 11/04/2016
f1_keywords:
- C3181
helpviewer_keywords:
- C3181
ms.assetid: 5d450f8b-6cef-4452-a0c4-2076e967451d
ms.openlocfilehash: dc848d4108ed4a1a7b6646647a1bbb1ec8dcadf7
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59779178"
---
# <a name="compiler-error-c3181"></a>Erreur du compilateur C3181

'type' : opérande non valide pour l’opérateur

Un paramètre non valide a été passé à la [typeid](../../extensions/typeid-cpp-component-extensions.md) opérateur. Le paramètre doit être un type managé.

Notez que le compilateur utilise des alias pour les types natifs qui mappent aux types dans le common language runtime.

L’exemple suivant génère l’erreur C3181 :

```
// C3181a.cpp
// compile with: /clr
using namespace System;

int main() {
   Type ^pType1 = interior_ptr<int>::typeid;   // C3181
   Type ^pType2 = int::typeid;   // OK
}
```
