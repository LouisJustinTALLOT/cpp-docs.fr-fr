---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4458'
title: Avertissement du compilateur (niveau 4) C4458
ms.date: 11/04/2016
f1_keywords:
- C4458
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
ms.openlocfilehash: f631fe4086c69732c972161ae7bb6096232b2740
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241259"
---
# <a name="compiler-warning-level-4-c4458"></a>Avertissement du compilateur (niveau 4) C4458

> la déclaration de'*identifier*'masque le membre de classe

La déclaration de l' *identificateur* dans la portée locale masque la déclaration de l' *identificateur* portant le même nom au niveau de la portée de la classe. Cet avertissement vous informe que les références à l' *identificateur* dans cette portée sont résolues à la version déclarée localement, et non à la version de membre de classe, qui peut être ou non votre intention. Pour résoudre ce problème, nous vous recommandons de fournir des noms de variables locales qui ne sont pas en conflit avec les noms de membres de classe.

## <a name="example"></a>Exemple

L’exemple suivant génère C4458, car le paramètre `x` et la variable locale `y` dans `member_fn` ont les mêmes noms que les membres de données de la classe. Pour résoudre ce problème, utilisez des noms différents pour les paramètres et les variables locales.

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```
