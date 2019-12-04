---
title: Erreur irrécupérable C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: 0feda3bc4c3729d3101be356220aa0124ba85190
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756940"
---
# <a name="fatal-error-c1017"></a>Erreur irrécupérable C1017

expression constante entière non valide

L’expression d’une directive de `#if` n’existe pas ou n’a pas été évaluée en constante.

Les constantes définies à l’aide de `#define` doivent avoir des valeurs qui correspondent à une constante entière si elles sont utilisées dans une directive `#if`, `#elif`ou `#else`.

L’exemple suivant génère l’C1017 :

```cpp
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Solution possible :

```cpp
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Étant donné que `CONSTANT_NAME` prend la valeur d’une chaîne et non d’un entier, la directive `#if` génère une erreur irrécupérable C1017.

Dans d’autres cas, le préprocesseur évalue une constante non définie comme zéro. Cela peut entraîner des résultats inattendus, comme illustré dans l’exemple suivant. `YES` n’est pas défini, il prend la valeur zéro. L’expression `#if` `CONSTANT_NAME` prend la valeur false et le code à utiliser sur `YES` est supprimé par le préprocesseur. `NO` est également non défini (zéro). par conséquent, `#elif` `CONSTANT_NAME==NO` prend la valeur true (`0 == 0`), ce qui amène le préprocesseur à conserver le code dans la partie `#elif` de l’instruction, exactement au contraire du comportement prévu.

```cpp
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Pour voir exactement comment le compilateur gère les directives de préprocesseur, utilisez [/p](../../build/reference/p-preprocess-to-a-file.md), [/e](../../build/reference/e-preprocess-to-stdout.md)ou [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).
