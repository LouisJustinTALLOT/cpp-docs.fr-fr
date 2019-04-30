---
title: Erreur du compilateur C2571
ms.date: 11/04/2016
f1_keywords:
- C2571
helpviewer_keywords:
- C2571
ms.assetid: c6522616-dee9-4d7d-9bf8-30a7e1deaadf
ms.openlocfilehash: d7d4898e5f0b55c50a4c18cef053cc150394d7e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408575"
---
# <a name="compiler-error-c2571"></a>Erreur du compilateur C2571

'fonction' : fonction virtuelle ne peut pas figurer dans l’union 'union'

Une union est déclarée avec une fonction virtuelle. Vous pouvez déclarer une fonction virtuelle uniquement dans une classe ou structure.  Solutions possibles :

1. Modifier l’union pour une classe ou structure.

1. Rendez la fonction non virtuelle.

L’exemple suivant génère l’erreur C2571 :

```
// C2571.cpp
// compile with: /c
union A {
   virtual void func1();   // C2571
   void func2();   // OK
};
```