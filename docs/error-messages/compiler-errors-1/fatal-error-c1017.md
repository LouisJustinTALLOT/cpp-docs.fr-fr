---
title: Erreur irrécupérable C1017
ms.date: 11/04/2016
f1_keywords:
- C1017
helpviewer_keywords:
- C1017
ms.assetid: 5542e604-599d-4e36-8f83-1d454c5753c9
ms.openlocfilehash: e2309b93be65b049c35abf96572e144a0a518007
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50614277"
---
# <a name="fatal-error-c1017"></a>Erreur irrécupérable C1017

expression constante entière non valide

L’expression dans une `#if` directive n’existe pas ou ne correspond pas à une constante.

Constantes définies à l’aide de `#define` doivent avoir des valeurs qui correspondent à une constante entière si elles sont utilisées dans un `#if`, `#elif`, ou `#else` directive.

L’exemple suivant génère l’erreur C1017 :

```
// C1017.cpp
#define CONSTANT_NAME "YES"
#if CONSTANT_NAME   // C1017
#endif
```

Solution possible :

```
// C1017b.cpp
// compile with: /c
#define CONSTANT_NAME 1
#if CONSTANT_NAME
#endif
```

Étant donné que `CONSTANT_NAME` prend la valeur d’une chaîne et non pas un entier, la `#if` directive génère l’erreur irrécupérable C1017.

Dans d’autres cas, le préprocesseur évalue une constante non définie en tant que zéro. Cela peut provoquer des résultats inattendus, comme indiqué dans l’exemple suivant. `YES` n’est pas défini, il correspond à zéro. L’expression `#if` `CONSTANT_NAME` prend la valeur false et le code à utiliser sur `YES` est supprimé par le préprocesseur. `NO` est également non défini (zéro), donc `#elif` `CONSTANT_NAME==NO` a la valeur true (`0 == 0`), à l’origine au préprocesseur de laisser le code dans la `#elif` partie de l’instruction — exactement l’inverse du comportement prévu.

```
// C1017c.cpp
// compile with: /c
#define CONSTANT_NAME YES
#if CONSTANT_NAME
   // Code to use on YES...
#elif CONSTANT_NAME==NO
   // Code to use on NO...
#endif
```

Pour voir exactement comment le compilateur gère les directives de préprocesseur, utilisez [/P](../../build/reference/p-preprocess-to-a-file.md), [/E](../../build/reference/e-preprocess-to-stdout.md), ou [/EP](../../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md).