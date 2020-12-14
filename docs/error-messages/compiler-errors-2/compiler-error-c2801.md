---
description: 'En savoir plus sur : erreur du compilateur C2801'
title: Erreur du compilateur C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: ca7e74f99b91b5a6699cdf3361ab64a89b7a7392
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297471"
---
# <a name="compiler-error-c2801"></a>Erreur du compilateur C2801

'operator opérateur’doit être un membre non static

Les opérateurs suivants peuvent être surchargés uniquement en tant que membres non statiques :

- Assigné `=`

- Accès au membre de classe `->`

- Indices `[]`

- Appel de fonction `()`

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
