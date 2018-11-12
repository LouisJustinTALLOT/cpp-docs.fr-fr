---
title: Erreur du compilateur C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: e377c18b5c0774a466dc535f2a1fba3411bd15b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50530245"
---
# <a name="compiler-error-c2790"></a>Erreur du compilateur C2790

'super' : ce mot clé peut uniquement être utilisé dans le corps de fonction membre de classe

Ce message d’erreur apparaît si l’utilisateur tente utilise le mot clé [super](../../cpp/super.md) en dehors du contexte d’une fonction membre.

L’exemple suivant génère l’erreur C2790 :

```
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```