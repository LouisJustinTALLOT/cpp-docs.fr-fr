---
description: 'En savoir plus sur : avertissement du compilateur C4694'
title: Avertissement du compilateur C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: f6a6890fab320c2471381076707eeca30ce3e99b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315073"
---
# <a name="compiler-warning-c4694"></a>Avertissement du compilateur C4694

> '*classe*' : une classe abstraite sealed ne peut pas avoir de classe de base'*BASE_CLASS*'

Une classe abstraite et sealed ne peut pas hériter d’un type référence ; elle ne peut pas non plus implémenter de fonctions de classe de base ou se laisser utiliser comme classe de base.

Pour plus d’informations, consultez [abstract](../../extensions/abstract-cpp-component-extensions.md), [sealed](../../extensions/sealed-cpp-component-extensions.md), [classes et structs](../../extensions/classes-and-structs-cpp-component-extensions.md).

Cet avertissement est automatiquement promu en erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma AVERTISSEMENT](../../preprocessor/warning.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4694.

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```
