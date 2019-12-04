---
title: Erreur du compilateur C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 85cac4919c048c30a3ed1ff5573a3c14b77da0bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737190"
---
# <a name="compiler-error-c2178"></a>Erreur du compilateur C2178

'*identifier*'ne peut pas être déclaré avec le spécificateur'*specifier*'

Un spécificateur de `mutable` a été utilisé dans une déclaration, mais le spécificateur n’est pas autorisé dans ce contexte.

Le spécificateur de `mutable` peut être appliqué uniquement aux noms des membres de données de classe et ne peut pas être appliqué à des noms déclarés `const` ou `static`, et ne peut pas être appliqué à des membres de référence.

## <a name="example"></a>Exemple

L’exemple suivant montre comment C2178 peut se produire et comment le résoudre.

```cpp
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
