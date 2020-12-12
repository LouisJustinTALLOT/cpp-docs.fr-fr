---
description: 'En savoir plus sur : erreur du compilateur C3866'
title: Erreur du compilateur C3866
ms.date: 11/04/2016
f1_keywords:
- C3866
helpviewer_keywords:
- C3866
ms.assetid: 685870af-2440-4cdf-a6cb-284a5b96ef9d
ms.openlocfilehash: fceb8ed41a3cbfc287f4c1115cd0502ce8506925
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97222864"
---
# <a name="compiler-error-c3866"></a>Erreur du compilateur C3866

liste d’arguments manquante dans l’appel de fonction

Dans une fonction membre non statique, un appel de destructeur ou de finaliseur n’a pas de liste d’arguments.

L’exemple suivant génère l’C3866 :

```cpp
// C3866.cpp
// compile with: /c
class C {
   ~C();
   void f() {
      this->~C;   // C3866
      this->~C();   // OK
   }
};
```
