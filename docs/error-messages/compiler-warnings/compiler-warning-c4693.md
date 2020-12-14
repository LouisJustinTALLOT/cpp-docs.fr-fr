---
description: 'En savoir plus sur : avertissement du compilateur C4693'
title: Avertissement du compilateur C4693
ms.date: 10/25/2017
f1_keywords:
- C4693
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
ms.openlocfilehash: 114809e1f73eb3d4e3481f0baa348d5eb478f4f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315099"
---
# <a name="compiler-warning-c4693"></a>Avertissement du compilateur C4693

> 'classe' : une classe abstraite sealed ne peut pas avoir de membres d’instance 'test'

Si un type est marqué comme [sealed](../../extensions/sealed-cpp-component-extensions.md) et [abstract](../../extensions/abstract-cpp-component-extensions.md), il ne peut avoir que des membres statiques.

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md).

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
