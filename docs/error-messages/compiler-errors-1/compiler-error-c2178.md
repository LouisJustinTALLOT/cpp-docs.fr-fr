---
description: 'En savoir plus sur : erreur du compilateur C2178'
title: Erreur du compilateur C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: 7a93293fdb87f30827b8b9c3c6d38066b0c76798
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97322160"
---
# <a name="compiler-error-c2178"></a>Erreur du compilateur C2178

'*identifier*'ne peut pas être déclaré avec le spécificateur'*specifier*'

Un **`mutable`** spécificateur a été utilisé dans une déclaration, mais le spécificateur n’est pas autorisé dans ce contexte.

Le **`mutable`** spécificateur peut être appliqué uniquement aux noms des membres de données de classe et ne peut pas être appliqué à des noms déclarés **`const`** ou **`static`** , et ne peut pas être appliqué à des membres de référence.

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
