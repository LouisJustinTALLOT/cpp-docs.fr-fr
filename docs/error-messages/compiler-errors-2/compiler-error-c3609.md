---
title: Erreur du compilateur C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 27eba3df800c42cc53a7031e958a675c84255440
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/05/2019
ms.locfileid: "58780975"
---
# <a name="compiler-error-c3609"></a>Erreur du compilateur C3609

'membre' : une fonction sealed ou final doit être virtuelle

Le [sealed](../../extensions/sealed-cpp-component-extensions.md) et [finale](../../cpp/final-specifier.md) mots clés sont uniquement autorisés sur une classe, struct ou une fonction membre marquée `virtual`.

L'exemple suivant génère l'erreur C3609 :

```
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
