---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4456'
title: Avertissement du compilateur (niveau 4) C4456
ms.date: 11/04/2016
f1_keywords:
- C4456
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
ms.openlocfilehash: f066de07b0c6bf7a7b5de3143909e402b0fedde3
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241311"
---
# <a name="compiler-warning-level-4-c4456"></a>Avertissement du compilateur (niveau 4) C4456

> la déclaration de'*identifier*'masque la déclaration locale précédente

La déclaration de l' *identificateur* dans la portée locale masque la déclaration de la déclaration locale précédente du même nom. Cet avertissement vous informe que les références à l' *identificateur* dans la portée locale sont résolues en version déclarée localement, et non dans la version locale précédente, qui peut être ou non votre intention. Pour résoudre ce problème, nous vous recommandons de fournir des noms de variables locales qui ne sont pas en conflit avec d’autres noms locaux.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4456, car la variable `int x` de contrôle de boucle et la variable locale `double x` dans `member_fn` ont le même nom. Pour résoudre ce problème, utilisez des noms différents pour les variables locales.

```cpp
// C4456_hide.cpp
// compile with: cl /W4 /c C4456_hide.cpp

struct S {
    void member_fn(unsigned u) {
        double x = 0;
        for (int x = 0; x < 10; ++x) {  // C4456
            u += x; // uses local int x
        }
        x += u; // uses local double x
    }
} s;
```
