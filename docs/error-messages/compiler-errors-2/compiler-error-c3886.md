---
title: Erreur du compilateur C3886
ms.date: 11/04/2016
f1_keywords:
- C3886
helpviewer_keywords:
- C3886
ms.assetid: 485f6c12-cc1b-4146-9034-409a0a5e615e
ms.openlocfilehash: e9e9d4b478d5b53e50203d1f009295e1da444f2d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402539"
---
# <a name="compiler-error-c3886"></a>Erreur du compilateur C3886

'var' : une donnée membre littérale doit être initialisée.

Un [littéral](../../extensions/literal-cpp-component-extensions.md) variable doit être initialisée lorsqu’elle est déclarée.

L’exemple suivant génère l’erreur C3886 :

```
// C3886.cpp
// compile with: /clr /c
ref struct Y1 {
   literal int staticConst;   // C3886
   literal int staticConst2 = 0;   // OK
};
```