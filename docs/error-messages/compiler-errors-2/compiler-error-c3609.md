---
title: Erreur du compilateur C3609
ms.date: 11/04/2016
f1_keywords:
- C3609
helpviewer_keywords:
- C3609
ms.assetid: 801e7f79-4ac6-4f8f-955f-703cdf095d00
ms.openlocfilehash: 2eff238aed756c9f056da9a1b9a70fca9de24fa3
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230803"
---
# <a name="compiler-error-c3609"></a>Erreur du compilateur C3609

'membre' : une fonction sealed ou final doit être virtuelle

Les mots clés [sealed](../../extensions/sealed-cpp-component-extensions.md) et [final](../../cpp/final-specifier.md) sont uniquement autorisés sur une classe, une structure ou une fonction membre marquée **`virtual`** .

L'exemple suivant génère l'erreur C3609 :

```cpp
// C3609.cpp
// compile with: /clr /c
ref class C {
   int f() sealed;   // C3609
   virtual int f2() sealed;   // OK
};
```
