---
title: Compilateur avertissement (niveau 4) C4457
ms.date: 11/04/2016
f1_keywords:
- C4457
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
ms.openlocfilehash: 11307ddc3b13a9cd9b36f1ee927082104792b07f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391437"
---
# <a name="compiler-warning-level-4-c4457"></a>Compilateur avertissement (niveau 4) C4457

> déclaration de '*identificateur*' paramètre de fonction de masque

La déclaration de *identificateur* dans l’étendue locale masque la déclaration du paramètre de fonction nommé de façon identique. Cet avertissement vous informe que les références à *identificateur* dans l’étendue locale correspondent à la version déclarée localement, pas le paramètre, qui peut être ou non votre intention. Pour résoudre ce problème, nous vous recommandons de que vous donner des noms de variables locales qui ne pas en conflit avec les noms de paramètres.

## <a name="example"></a>Exemple

L’exemple suivant génère le C4457, car le paramètre `x` et la variable locale `x` dans `member_fn` ont les mêmes noms. Pour résoudre ce problème, utilisez des noms différents pour les paramètres et les variables locales.

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
