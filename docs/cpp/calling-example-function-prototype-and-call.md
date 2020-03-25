---
title: "Exemple d'appel : Prototype et appel de fonction"
ms.date: 11/04/2016
helpviewer_keywords:
- calling conventions, examples [C++]
- examples [C++], calling conventions
ms.assetid: e4275d1f-df2e-4bfc-a162-eb43ec69554a
ms.openlocfilehash: c41d7679be8b7faa3c8df1368d14815a1b840284
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190168"
---
# <a name="calling-example-function-prototype-and-call"></a>Exemple d'appel : Prototype et appel de fonction

**Section spécifique de Microsoft**

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

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[Conventions d’appel](../cpp/calling-conventions.md)
