---
title: Erreur du compilateur C2106
ms.date: 11/04/2016
f1_keywords:
- C2106
helpviewer_keywords:
- C2106
ms.assetid: d5c91a2e-04e4-4770-8478-788b98c52a53
ms.openlocfilehash: 6a82792c8a8acfd0d397e02929a457aae8ef7050
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50507570"
---
# <a name="compiler-error-c2106"></a>Erreur du compilateur C2106

'opérateur' : opérande gauche doit être l-value

L’opérateur doit avoir une l-value comme opérande gauche.

L’exemple suivant génère l’erreur C2106 :

```
// C2106.cpp
int main() {
   int a;
   1 = a;   // C2106
   a = 1;   // OK
}
```