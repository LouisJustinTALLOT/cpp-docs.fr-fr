---
description: 'En savoir plus sur : erreur du compilateur C2571'
title: Erreur du compilateur C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: 773cab05204e15a22a4412364bd8f89cddfd92ea
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97208968"
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
