---
title: Erreur du compilateur C2111
ms.date: 11/04/2016
f1_keywords:
- C2111
helpviewer_keywords:
- C2111
ms.assetid: 38fd42ec-1480-4a44-aaca-ae4593ed5f50
ms.openlocfilehash: 193fa787c8e6beb0d4a45f419d3af3baf7988cc1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757811"
---
# <a name="compiler-error-c2111"></a>Erreur du compilateur C2111

'+' : l’addition d’un pointeur exige un opérande de type entier

Une tentative a été effectuée d’ajouter une valeur non entière à un pointeur avec l’opérateur plus ( `+` ).

L’exemple suivant génère l’erreur C2111 :

```cpp
// C2111.cpp
int main() {
   int *a = 0, *pa = 0, b = 0;
   double d = 0.00;

   a = pa + d;   // C2111
   a = pa + b;   // OK
}
```
