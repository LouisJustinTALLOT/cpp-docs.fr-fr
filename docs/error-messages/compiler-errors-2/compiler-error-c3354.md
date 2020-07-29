---
title: Erreur du compilateur C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: fdc5de7493decf1f44617ab22a00fb5e8852116f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231973"
---
# <a name="compiler-error-c3354"></a>Erreur du compilateur C3354

'fonction' : la fonction utilisée pour créer un délégué ne peut pas avoir un type de retour 'type'

Les types suivants ne sont pas valides en tant que types de retour pour un **`delegate`** :

- Pointeur vers fonction

- Pointeur vers membre

- Pointeur vers fonction membre

- Référence vers fonction

- Référence vers fonction membre

L’exemple suivant génère l’erreur C3354 :

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
