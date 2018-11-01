---
title: Erreur du compilateur C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: 1ff2967f602722c99b58b679324bd4f50575f109
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50523156"
---
# <a name="compiler-error-c3354"></a>Erreur du compilateur C3354

'fonction' : la fonction utilisée pour créer un délégué ne peut pas avoir un type de retour 'type'

Les types suivants ne sont pas des types de retour valides pour un `delegate`:

- Pointeur vers fonction

- Pointeur vers membre

- Pointeur vers fonction membre

- Référence vers fonction

- Référence vers fonction membre

L’exemple suivant génère l’erreur C3354 :

```
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
