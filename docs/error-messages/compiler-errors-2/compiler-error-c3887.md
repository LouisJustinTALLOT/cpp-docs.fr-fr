---
title: Erreur du compilateur C3887 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3887
dev_langs:
- C++
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1238f648c7e5481127562d34dde193a278c3cf0f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047627"
---
# <a name="compiler-error-c3887"></a>Erreur du compilateur C3887

'var' : l’initialiseur d’une donnée membre littérale doit être une expression constante

Un [littéral](../../windows/literal-cpp-component-extensions.md) données membre peut uniquement être initialisée avec une expression constante.

L’exemple suivant génère l’erreur C3887 :

```
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

Solution possible :

```
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```