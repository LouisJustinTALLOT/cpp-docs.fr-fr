---
title: Erreur du compilateur C3887
ms.date: 11/04/2016
f1_keywords:
- C3887
helpviewer_keywords:
- C3887
ms.assetid: a7e82426-ef99-437b-9562-2822004e18fe
ms.openlocfilehash: f64b72fe5d546550c32f60a27360d8a77c8255bd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74736579"
---
# <a name="compiler-error-c3887"></a>Erreur du compilateur C3887

'var' : l’initialiseur d’une donnée membre littérale doit être une expression constante

Une donnée membre [littérale](../../extensions/literal-cpp-component-extensions.md) ne peut être initialisée qu’avec une impossibilité de constante.

L’exemple suivant génère l’C3887 :

```cpp
// C3887.cpp
// compile with: /clr
ref struct Y1 {
   static int i = 9;
   literal
   int staticConst = i;   // C3887
};
```

Solution possible :

```cpp
// C3887b.cpp
// compile with: /clr /c
ref struct Y1 {
   literal
   int staticConst = 9;
};
```
