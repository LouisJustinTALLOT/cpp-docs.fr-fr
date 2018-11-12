---
title: Erreur du compilateur C2801
ms.date: 11/04/2016
f1_keywords:
- C2801
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
ms.openlocfilehash: 44f7988f9fedb882972b2823f2fe70d9512d4e87
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484784"
---
# <a name="compiler-error-c2801"></a>Erreur du compilateur C2801

'operator opérateur' doit être un membre non static

Les opérateurs suivants peuvent être surchargées uniquement en tant que membres non statiques :

- Affectation `=`

- Accès au membre de classe `->`

- Mettre en indice `[]`

- Appel de fonction `()`

Causes possibles de l’erreur C2801 :

- Opérateur surchargé n’est pas une classe, une structure ou un membre d’union.

- Opérateur surchargé est déclaré `static`.

- L’exemple suivant génère l’erreur C2801 :

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```