---
title: Erreur du compilateur C2798
ms.date: 11/04/2016
f1_keywords:
- C2798
helpviewer_keywords:
- C2798
ms.assetid: fb0cd861-b228-4f81-8090-e28344a727e0
ms.openlocfilehash: f3e8f0ac260e49866d1c654f89d34bf57a8ffbc1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50463052"
---
# <a name="compiler-error-c2798"></a>Erreur du compilateur C2798

'super::membre' est ambigu

Plusieurs structures héritées contiennent le membre que vous avez référencé avec [super](../../cpp/super.md). Vous pouvez corriger l’erreur à l’aide :

- Suppression de B1 ou B2 dans la liste d’héritage de D.

- Modification du nom du membre de données dans B1 ou B2.

L’exemple suivant génère l’erreur C2798 :

```
// C2798.cpp
struct B1 {
   int i;
};

struct B2 {
   int i;
};

struct D : B1, B2 {
   void g() {
      __super::i = 4; // C2798
   }
};
```