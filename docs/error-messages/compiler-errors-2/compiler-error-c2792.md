---
description: 'En savoir plus sur : erreur du compilateur C2792'
title: Erreur du compilateur C2792
ms.date: 11/04/2016
f1_keywords:
- C2792
helpviewer_keywords:
- C2792
ms.assetid: 392cf748-4f5e-4e62-a364-3118d5658408
ms.openlocfilehash: 5699f734574aaadd01aa6ddabac09facc249fb1d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97297757"
---
# <a name="compiler-error-c2792"></a>Erreur du compilateur C2792

'Super' : ce mot clé doit être suivi de' :: '

Le seul jeton qui peut suivre le mot clé **`__super`** est `::` .

L’exemple suivant génère l’C2792 :

```cpp
// C2792.cpp
struct B {
   void mf();
};

struct D : B {
   void mf() {
      __super.();   // C2792

      // try the following line instead
      // __super::mf();
   }
};
```
