---
title: Avertissement du compilateur C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: daf5423588d08260239c3cff5a68532a358d07b2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80165117"
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
