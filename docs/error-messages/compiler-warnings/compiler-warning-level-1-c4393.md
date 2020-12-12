---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4393'
title: Avertissement du compilateur (niveau 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: e68829b7e41cbc1720ceb4dced374a53e97fe8d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97212712"
---
# <a name="compiler-warning-level-1-c4393"></a>Avertissement du compilateur (niveau 1) C4393

'var' : const n’a aucun effet sur les données membres littérales ; pas

Une donnée membre [littérale](../../extensions/literal-cpp-component-extensions.md) a également été spécifiée comme const.  Étant donné qu’un membre de données littéral implique const, vous n’avez pas besoin d’ajouter const à la déclaration.

L’exemple suivant génère l’C4393 :

```cpp
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```
