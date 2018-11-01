---
title: Erreur du compilateur C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 5572f39082e2dcd8746bb464595c5c00e2f77356
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50556441"
---
# <a name="compiler-error-c3609"></a>Erreur du compilateur C3609

'membre' : une fonction sealed ou final doit être virtuelle

Le [sealed](../../windows/sealed-cpp-component-extensions.md) et [finale](../../cpp/final-specifier.md) mots clés sont uniquement autorisés sur une classe, struct ou une fonction membre marquée `virtual`.

L'exemple suivant génère l'erreur C3609 :

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
