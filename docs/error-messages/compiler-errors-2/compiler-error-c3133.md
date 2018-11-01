---
title: Erreur du compilateur C3133
ms.date: 11/04/2016
f1_keywords:
- C3133
helpviewer_keywords:
- C3133
ms.assetid: 4a709405-b67b-4061-8a2a-19fa5fb34a2a
ms.openlocfilehash: 54683f97000bb1467d2cd93376ee8db77fd0685c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50532689"
---
# <a name="compiler-error-c3133"></a>Erreur du compilateur C3133

Les attributs ne peuvent pas être appliqués aux varargs C++

Un attribut a été appliqué de façon incorrecte. Attributs ne peuvent pas être appliqués à des points de suspension représentant les arguments de variables.

Pour plus d'informations, consultez [User-Defined Attributes](../../windows/user-defined-attributes-cpp-component-extensions.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3133.

```
// C3133.cpp
// compile with: /clr /c
ref struct MyAttr: System::Attribute {};
void Func([MyAttr]...);   // C3133
void Func2([MyAttr] int i);   // OK
```