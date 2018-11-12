---
title: Compilateur avertissement (niveau 4) C4458
ms.date: 11/04/2016
f1_keywords:
- C4458
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
ms.openlocfilehash: 9e5eb8dc44968332abc097bfbd16b48e3240695c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50500982"
---
# <a name="compiler-warning-level-4-c4458"></a>Compilateur avertissement (niveau 4) C4458

> déclaration de '*identificateur*' masque le membre de classe

La déclaration de *identificateur* dans l’étendue locale masque la déclaration de la portant *identificateur* à portée de classe. Cet avertissement vous informe que les références à *identificateur* dans cette portée correspondent à la version déclarée localement, pas la classe membre version, ce qui peut ou peut ne pas être votre intention. Pour résoudre ce problème, nous vous recommandons de que vous donner des noms de variables locales qui ne pas en conflit avec les noms de membres de classe.

## <a name="example"></a>Exemple

L’exemple suivant génère le C4458, car le paramètre `x` et la variable locale `y` dans `member_fn` ont les mêmes noms que les membres de données dans la classe. Pour résoudre ce problème, utilisez des noms différents pour les paramètres et les variables locales.

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
