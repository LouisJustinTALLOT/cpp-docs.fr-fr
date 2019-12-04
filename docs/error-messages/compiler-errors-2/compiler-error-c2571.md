---
title: Erreur du compilateur C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: 7bd87f0732e1a632b8c86cc57fab1a0f104b2c77
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755497"
---
# <a name="compiler-error-c2571"></a>Erreur du compilateur C2571

'fonction' : la fonction virtuelle ne peut pas être dans l’Union’Union'

Une Union est déclarée avec une fonction virtuelle. Vous pouvez déclarer une fonction virtuelle uniquement dans une classe ou une structure.  Solutions possibles :

1. Remplacez l’Union par une classe ou une structure.

1. Rendez la fonction qui n’est pas virtuelle.

L’exemple suivant génère l’C2571 :

```cpp
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```
