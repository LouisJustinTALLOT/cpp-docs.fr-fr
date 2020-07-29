---
title: Expressions constantes C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 32d14650450d8047a5bc0e6cf7bb06788c9b3d81
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221755"
---
# <a name="c-constant-expressions"></a>Expressions constantes C++

Une valeur *constante* est une valeur qui ne change pas. C++ fournit deux mots clés qui vous permettent d'exprimer l'intention qu'un objet n'est pas destiné à être modifié, et d'appliquer cette intention.

C++ requiert des expressions constantes (expressions qui ont pour valeur une constante) pour les déclarations des éléments suivants :

- Limites d'index de tableau

- Sélecteurs dans les instructions case

- Spécification de longueur de champ de bits

- Initialiseurs d'énumération

Les seuls opérandes autorisés dans les expressions constantes sont :

- Littéraux

- Constantes d'énumération

- Valeurs déclarées comme const qui sont initialisées avec des expressions constantes

- **`sizeof`** manifestations

Les constantes non intégrales doivent être converties (explicitement ou implicitement) en types intégraux pour être autorisées dans une expression constante. Par conséquent, le code suivant est conforme :

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Les conversions explicites en types intégraux sont autorisées dans les expressions constantes ; tous les autres types et types dérivés sont illégaux, sauf lorsqu’ils sont utilisés comme opérandes de l' **`sizeof`** opérateur.

L'opérateur virgule et les opérateurs d'assignation de virgule ne peuvent pas être utilisés dans les expressions constantes.

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)
