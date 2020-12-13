---
description: 'En savoir plus sur : exemple d’appel : prototype et appel de fonction'
title: "Exemple d'appel : Prototype et appel de fonction"
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: d7d8b68abc030e12d10fc5daa8b56f793d3ea14a
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335588"
---
# <a name="calling-example-function-prototype-and-call"></a>Exemple d'appel : Prototype et appel de fonction

**Spécifique à Microsoft**

L’exemple suivant montre les résultats d’un appel de fonction effectué à l’aide de différentes conventions d’appel.

Cet exemple repose sur la structure de fonction suivante. Remplacez `calltype` par la convention d'appel appropriée.

```cpp
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

Pour plus d’informations, consultez [résultats de l’appel de l’exemple](../cpp/results-of-calling-example.md).

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
