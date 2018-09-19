---
title: Compilateur avertissement (niveau 4) C4458 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4458
dev_langs:
- C++
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 873aa94db899ae6620e2bbb1f24277c6e7c841c4
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094544"
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
