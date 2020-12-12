---
description: 'En savoir plus sur : erreur du compilateur C2624'
title: Erreur du compilateur C2624
ms.date: 11/04/2016
f1_keywords:
- C2624
helpviewer_keywords:
- C2624
ms.assetid: 32f2ec15-a7cd-4049-a64b-131746d3152b
ms.openlocfilehash: 4fa52e5192bd71c9fcdd3608b4161d1e5da57bdf
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97174674"
---
# <a name="compiler-error-c2624"></a>Erreur du compilateur C2624

les classes locales ne peuvent pas être utilisées pour déclarer des variables’extern'

Une classe ou une structure locale ne peut pas être utilisée pour déclarer des **`extern`** variables.

L’exemple suivant génère l’C2624 :

```cpp
// C2624.cpp
int main() {
   struct C {};
   extern C ac;   // C2624
}
```
