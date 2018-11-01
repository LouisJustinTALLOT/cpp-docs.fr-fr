---
title: "Exemple d'appel : Prototype et appel de fonction"
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: f89f4f1917810baa585dd1661428e0809b93cca0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508180"
---
# <a name="calling-example-function-prototype-and-call"></a>Exemple d'appel : Prototype et appel de fonction

## <a name="microsoft-specific"></a>Section spécifique à Microsoft

L’exemple suivant montre les résultats d’un appel de fonction effectué à l’aide de différentes conventions d’appel.

Cet exemple repose sur la structure de fonction suivante. Remplacez `calltype` par la convention d’appel appropriée.

```
void    calltype MyFunc( char c, short s, int i, double f );
.
.
.
void    MyFunc( char c, short s, int i, double f )
    {
    .
    .
    .
    }
.
.
.
MyFunc ('x', 12, 8192, 2.7183);
```

Pour plus d’informations, consultez [résultats de l’exemple appel](../cpp/results-of-calling-example.md).

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)