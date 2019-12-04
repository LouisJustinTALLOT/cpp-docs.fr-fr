---
title: Erreur du compilateur C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 0d2ea3677d883fa4843c37a41d733872b23cbba0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760671"
---
# <a name="compiler-error-c2801"></a>Erreur du compilateur C2801

'operator opérateur’doit être un membre non static

Les opérateurs suivants peuvent être surchargés uniquement en tant que membres non statiques :

- `=` d’affectation

- `->` d’accès au membre de classe

- `[]` de script

- Appel de fonction `()`

Causes possibles de C2801 :

- L’opérateur surchargé n’est pas un membre de classe, de structure ou d’Union.

- L’opérateur surchargé est déclaré `static`.

- L’exemple suivant génère l’C2801 :

```cpp
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```
