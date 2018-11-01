---
title: Avertissement du compilateur C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 49d101ea56cd868e18489b6c74724a2d106c9265
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536654"
---
# <a name="compiler-warning-c4693"></a>Avertissement du compilateur C4693

> 'classe' : une classe abstraite sealed ne peut pas avoir de membres d’instance 'test'

Si un type est marqué [sealed](../../windows/sealed-cpp-component-extensions.md) et [abstraite](../../windows/abstract-cpp-component-extensions.md), il peut comporter uniquement des membres statiques.

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4693.

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```