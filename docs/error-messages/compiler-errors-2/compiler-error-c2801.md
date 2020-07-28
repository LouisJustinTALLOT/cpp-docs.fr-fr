---
title: Erreur du compilateur C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: cfb89c79534318ab1fbcaa06667d594bfe2f1157
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214592"
---
# <a name="compiler-error-c2801"></a>Erreur du compilateur C2801

'operator opérateur’doit être un membre non static

Les opérateurs suivants peuvent être surchargés uniquement en tant que membres non statiques :

- Assigné`=`

- Accès au membre de classe`->`

- Indices`[]`

- Appel de fonction`()`

Causes possibles de C2801 :

- L’opérateur surchargé n’est pas un membre de classe, de structure ou d’Union.

- L’opérateur surchargé est déclaré **`static`** .

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
