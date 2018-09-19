---
title: Compilateur avertissement (niveau 4) C4457 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4457
dev_langs:
- C++
helpviewer_keywords:
- C4457
ms.assetid: 02fd149a-917d-4f67-97a6-eb714572271f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 62232a814bed47f8b6a5041d20e6f37776abffe8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093530"
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
