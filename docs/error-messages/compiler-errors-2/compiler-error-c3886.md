---
title: Erreur du compilateur C3886
ms.date: 11/04/2016
f1_keywords:
- C3886
helpviewer_keywords:
- C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
ms.openlocfilehash: 2e7ba0fcc76d723cebb5b82315faf36313b1d7db
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736631"
---
# <a name="compiler-error-c3886"></a>Erreur du compilateur C3886

'var' : une donnée membre littérale doit être initialisée

Une variable [littérale](../../extensions/literal-cpp-component-extensions.md) doit être initialisée lorsqu’elle est déclaraie.

L’exemple suivant génère l’C3886 :

```cpp
// C3886.cpp
// compile with: /clr /c
ref struct Y1 {
   literal int staticConst;   // C3886
   literal int staticConst2 = 0;   // OK
};
```
