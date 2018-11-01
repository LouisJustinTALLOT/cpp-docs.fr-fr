---
title: Avertissement du compilateur C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: 6eaaa4c1f16e2ac2c5029511430a145fd9b943e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50428338"
---
# <a name="compiler-warning-c4694"></a>Avertissement du compilateur C4694

> «*classe*' : une classe abstraite sealed ne peut pas avoir une classe de base*base_class*»

Une classe abstraite et sealed ne peut pas hériter d’un type référence ; elle ne peut pas non plus implémenter de fonctions de classe de base ou se laisser utiliser comme classe de base.

Pour plus d’informations, consultez [abstraite](../../windows/abstract-cpp-component-extensions.md), [sealed](../../windows/sealed-cpp-component-extensions.md), et [les Classes et Structs](../../windows/classes-and-structs-cpp-component-extensions.md).

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```