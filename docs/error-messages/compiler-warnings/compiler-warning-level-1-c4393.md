---
title: Avertissement du compilateur (niveau 1) C4393
ms.date: 11/04/2016
f1_keywords:
- C4393
helpviewer_keywords:
- C4393
ms.assetid: 353a0539-d1ea-4c1b-8849-c9b321ec9842
ms.openlocfilehash: 21ea45963c7e3d2afe74ebf4aa5207629ec9c8db
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50594247"
---
# <a name="compiler-warning-level-1-c4393"></a>Avertissement du compilateur (niveau 1) C4393

'var' : const n’a aucun effet sur la donnée membre littérale ; ignoré

Un [littéral](../../windows/literal-cpp-component-extensions.md) membre de données a été également spécifié en tant que const.  Dans la mesure où une donnée membre littérale implique const, il est inutile ajouter const à la déclaration.

L’exemple suivant génère l’erreur C4393 :

```
// C4393.cpp
// compile with: /clr /W1 /c
ref struct Y1 {
   literal const int staticConst = 10;   // C4393
   literal int staticConst2 = 10;   // OK
};
```