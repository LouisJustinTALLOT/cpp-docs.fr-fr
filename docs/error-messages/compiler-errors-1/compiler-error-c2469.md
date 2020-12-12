---
description: 'En savoir plus sur : erreur du compilateur C2469'
title: Erreur du compilateur C2469
ms.date: 11/04/2016
f1_keywords:
- C2469
helpviewer_keywords:
- C2469
ms.assetid: 3814bdff-581a-4d3e-8b47-8de6887cea69
ms.openlocfilehash: 861b023d4233343458957a0e4ed51c94a9dd4625
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97164547"
---
# <a name="compiler-error-c2469"></a>Erreur du compilateur C2469

'operator' : impossible d’allouer l’objet 'type'

Un type non valide a été passé à un opérateur.

L’exemple suivant génère l’erreur C2469 :

```cpp
// C2469.cpp
int main() {
   int *i = new void;   // C2469
   int *i = new int;   // OK
}
```
