---
title: Erreur du compilateur C3354
ms.date: 11/04/2016
f1_keywords:
- C3354
helpviewer_keywords:
- C3354
ms.assetid: 185de401-231e-4999-a149-172ee4c69d84
ms.openlocfilehash: e5945b2112d1d03e4f18944d15028229cce4b668
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74738594"
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

```cpp
// C3354_2.cpp
// compile with: /clr /c
using namespace System;
typedef void ( *VoidPfn )();

delegate VoidPfn func(); // C3354
// try the following line instead
// delegate  void func();
```
