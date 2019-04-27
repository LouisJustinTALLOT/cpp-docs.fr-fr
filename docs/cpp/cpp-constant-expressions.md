---
title: Expressions constantes C++
ms.date: 11/04/2016
helpviewer_keywords:
- constant expressions, syntax
- constant expressions
- expressions [C++], constant
ms.assetid: b07245a5-4c21-4589-b503-e6ffd631996f
ms.openlocfilehash: 97059066adadc3a7897cbd2c4c747e2a673e7201
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154670"
---
# <a name="c-constant-expressions"></a>Expressions constantes C++

Un *constante* valeur fait partie qui ne change pas. C++ fournit deux mots clés qui vous permettent d'exprimer l'intention qu'un objet n'est pas destiné à être modifié, et d'appliquer cette intention.

C++ requiert des expressions constantes (expressions qui ont pour valeur une constante) pour les déclarations des éléments suivants :

- Limites d'index de tableau

- Sélecteurs dans les instructions case

- Spécification de longueur de champ de bits

- Initialiseurs d'énumération

Les seuls opérandes autorisés dans les expressions constantes sont :

- Littéraux

- Constantes d'énumération

- Valeurs déclarées comme const qui sont initialisées avec des expressions constantes

- **sizeof** expressions

Les constantes non intégrales doivent être converties (explicitement ou implicitement) en types intégraux pour être autorisées dans une expression constante. Par conséquent, le code suivant est conforme :

```cpp
const double Size = 11.0;
char chArray[(int)Size];
```

Les conversions explicites en types intégraux sont autorisées dans les expressions constantes ; tous les autres types et les types dérivés ne sont pas conformes, sauf lorsque utilisé en tant qu’opérandes pour le **sizeof** opérateur.

L'opérateur virgule et les opérateurs d'assignation de virgule ne peuvent pas être utilisés dans les expressions constantes.

## <a name="see-also"></a>Voir aussi

[Types d’expressions](../cpp/types-of-expressions.md)