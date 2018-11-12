---
title: Erreur du compilateur C2178
ms.date: 05/08/2017
f1_keywords:
- C2178
helpviewer_keywords:
- C2178
ms.assetid: 79a14158-17f3-4221-bd06-9d675c49cef4
ms.openlocfilehash: cd153bb5b331872bfe35b046d41612998bd0eff7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622558"
---
# <a name="compiler-error-c2178"></a>Erreur du compilateur C2178

«*identificateur*'ne peut pas être déclarée avec'*spécificateur*' spécificateur

Un `mutable` spécificateur a été utilisé dans une déclaration, mais le spécificateur n’est pas autorisé dans ce contexte.

Le `mutable` spécificateur peut être appliqué uniquement à des noms de membres de données de classe et ne peut pas être appliqué à des noms déclarés `const` ou `static`et ne peut pas être appliqué pour référencer des membres.

## <a name="example"></a>Exemple

L’exemple suivant montre comment C2178 peut se produire et comment la corriger.

```
// C2178.cpp
// compile with: cl /c /W4 C2178.cpp

class S {
    mutable const int i; // C2178
    // To fix, declare either const or mutable, not both.
};

mutable int x = 4; // C2178
// To fix, remove mutable keyword
```
