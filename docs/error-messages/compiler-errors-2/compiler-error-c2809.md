---
title: Erreur du compilateur C2809
ms.date: 11/04/2016
f1_keywords:
- C2809
helpviewer_keywords:
- C2809
ms.assetid: ce796b8e-1a8c-4074-995d-1ad09afd0e93
ms.openlocfilehash: d9dffabf318d51a97c172ecee2e4b2d4183a81f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640672"
---
# <a name="compiler-error-c2809"></a>Erreur du compilateur C2809

'operator opérateur' n’a aucun paramètre formel

L’opérateur ne dispose pas des paramètres requis.

L’exemple suivant génère l’erreur C2809 :

```
// C2809.cpp
// compile with: /c
class A{};
int operator+ ();   // C2809
int operator+ (A);   // OK
```