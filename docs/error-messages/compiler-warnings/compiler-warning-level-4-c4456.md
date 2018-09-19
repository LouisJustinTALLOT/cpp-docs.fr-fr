---
title: Compilateur avertissement (niveau 4) C4456 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4456
dev_langs:
- C++
helpviewer_keywords:
- C4456
ms.assetid: 5ab39fc1-0e19-461b-842b-4da80560b044
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9ab6939fe37260b906a43c4e2ff6683733348952
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46039892"
---
# <a name="compiler-warning-level-4-c4456"></a>Compilateur avertissement (niveau 4) C4456

> déclaration de '*identificateur*' masque la déclaration locale précédente

La déclaration de *identificateur* dans l’étendue locale masque la déclaration de la déclaration locale précédente du même nom. Cet avertissement vous informe que les références à *identificateur* dans l’étendue locale correspondent à la version déclarée localement, pas précédente local, ce qui peut ou peut ne pas être votre intention. Pour résoudre ce problème, nous vous recommandons de que vous donner des noms de variables locales qui ne pas en conflit avec d’autres noms locaux.

## <a name="example"></a>Exemple

L’exemple suivant génère le C4456, car la boucle contrôler variable `int x` et la variable locale `double x` dans `member_fn` ont les mêmes noms. Pour résoudre ce problème, utilisez des noms différents pour les variables locales.

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
