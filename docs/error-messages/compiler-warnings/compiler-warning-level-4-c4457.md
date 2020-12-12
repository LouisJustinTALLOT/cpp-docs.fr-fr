---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4457'
title: Avertissement du compilateur (niveau 4) C4457
ms.date: 11/04/2016
f1_keywords:
- C4457
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
ms.openlocfilehash: 8898189668eba95619e6bd0d0ccf1cb8ca3afdfe
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97251412"
---
# <a name="compiler-warning-level-4-c4457"></a>Avertissement du compilateur (niveau 4) C4457

> la déclaration de'*identifier*'masque le paramètre de fonction

La déclaration de l' *identificateur* dans la portée locale masque la déclaration du paramètre de fonction portant le même nom. Cet avertissement vous informe que les références à l' *identificateur* dans la portée locale sont résolues en version déclarée localement, et non pas au paramètre, qui peut être ou non votre intention. Pour résoudre ce problème, nous vous recommandons de fournir des noms de variables locales qui ne sont pas en conflit avec les noms de paramètres.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4457, car le paramètre `x` et la variable locale `x` dans `member_fn` ont le même nom. Pour résoudre ce problème, utilisez des noms différents pour les paramètres et les variables locales.

```cpp
// C4457_hide.cpp
// compile with: cl /W4 /c C4457_hide.cpp

struct S {
    void member_fn(unsigned x) {
        double a = 0;
        for (int x = 0; x < 10; ++x) {  // C4457
            a += x; // uses local x
        }
        a += x; // uses parameter x
    }
} s;
```
